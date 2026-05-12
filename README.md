/**
 * Licensed to the Apache Software Foundation (ASF) under one
 * or more contributor license agreements.  See the NOTICE file
 * distributed with this work for additional information
 * regarding copyright ownership.  The ASF licenses this file
 * to you under the Apache License, Version 2.0 (the
 * "License"); you may not use this file except in compliance
 * with the License.  You may obtain a copy of the License at
 *
 *   http://www.apache.org/licenses/LICENSE-2.0
 *
 * Unless required by applicable law or agreed to in writing,
 * software distributed under the License is distributed on an
 * "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
 * KIND, either express or implied.  See the License for the
 * specific language governing permissions and limitations
 * under the License.
 */
import { useEffect, useRef, useState, useCallback, useMemo } from 'react';
import { useHistory } from 'react-router-dom';
import { SupersetClient, styled, t, JsonObject } from '@superset-ui/core';
import {
  DeleteModal,
  ListViewCard,
  Loading,
} from '@superset-ui/core/components';
import { ImportModal as ImportModelsModal } from 'src/components/ImportModal';
import { Icons } from '@superset-ui/core/components/Icons';
import rison from 'rison';
import withToasts from 'src/components/MessageToasts/withToasts';
import { CardContainer, loadingCardCount } from 'src/views/CRUD/utils';
import { TableTab } from 'src/views/CRUD/types';
import { findPermission } from 'src/utils/findPermission';
import InsightsViewHeader from 'src/pages/DashboardList/InsightsViewHeader';
import { DASHBOARD_CATEGORIES } from 'src/dashboard/constants/categories';
import { navigateTo } from 'src/utils/navigationUtils';
import { useFavoriteStatus } from 'src/views/CRUD/hooks';
import { Dashboard } from 'src/views/CRUD/types';
import DashboardCard from 'src/features/dashboards/DashboardCard';
import PropertiesModal from 'src/dashboard/components/PropertiesModal';
import handleResourceExport from 'src/utils/export';

/* ── Category icons ── */
const CATEGORY_ICONS: Record<string, React.ReactNode> = {
   'Business Strategy': <Icons.FundProjectionScreenOutlined iconSize="l" />,
  'Agent Empowerment': <Icons.UsergroupAddOutlined iconSize="l" />,
  'CX and Journey': <Icons.LineChartOutlined iconSize="l" />,
  'Performance Cockpit': <Icons.DashboardOutlined iconSize="l" />,
};

/* ── Dashboard type (lightweight, only what we need) ── */
type DashboardItem = Dashboard;

/* ══════════════════════════════════════════════════════
   Styled Components
   ══════════════════════════════════════════════════════ */

/* Same gradient as InsightsViews (DashboardList) – single wrapper, extends with content */
const PageContainer = styled.div`
  font-family: 'Poppins', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto,
    sans-serif;
  min-height: 100%;
  height: 100%;
  width: 100%;
  overflow-x: hidden;
  background:
    radial-gradient(
      ellipse at 0% 100%,
      rgba(93, 192, 216, 0.08) 0%,
      transparent 50%
    ),
    radial-gradient(
      ellipse at 100% 0%,
      rgba(212, 238, 245, 0.12) 0%,
      transparent 40%
    ),
    radial-gradient(
      ellipse at 100% 100%,
      rgba(125, 211, 232, 0.06) 0%,
      transparent 30%
    ),
    radial-gradient(
      ellipse at 0% 0%,
      rgba(232, 244, 248, 0.1) 0%,
      transparent 35%
    ),
    linear-gradient(180deg, #ffffff 0%, #f8fcfd 100%);
`;

/* ── Category sections container (same pattern as ListView: transparent so gradient shows through) ── */
const CategoriesContainer = styled.div`
  padding: 32px 48px 48px;
  display: flex;
  flex-direction: column;
  gap: 40px;
  background: transparent;
  position: relative;
  z-index: 1;

  @media (max-width: 768px) {
    padding: 24px 20px 32px;
    gap: 32px;
  }
`;

/* ── Single category section ── */
const CategorySection = styled.div`
  display: flex;
  flex-direction: column;
  gap: 16px;
  padding: 24px 24px 28px;
  border-radius: 16px;
  background: transparent;
`;

const CategoryHeader = styled.div`
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 16px;
`;

const CategoryTitleWrapper = styled.div`
  display: flex;
  align-items: center;
  gap: 12px;
`;

const CategoryIcon = styled.div`
  width: 40px;
  height: 40px;
  border-radius: 10px;
  background: linear-gradient(135deg, #005071 0%, #5191cd 100%);
  display: flex;
  align-items: center;
  justify-content: center;

  svg,
  span {
    color: #ffffff !important;
  }
`;

const CategoryTitle = styled.h2`
  font-family: 'Poppins', sans-serif;
  font-size: 20px;
  font-weight: 600;
  color: #333333;
  margin: 0;
`;

const CategoryCount = styled.span`
  font-family: 'Poppins', sans-serif;
  font-size: 13px;
  font-weight: 400;
  color: #999999;
  margin-left: 8px;
`;

/* ── Collapse/Expand button ── */
const CollapseButton = styled.button<{ isCollapsed: boolean }>`
  background: transparent;
  border: none;
  cursor: pointer;
  padding: 8px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 6px;
  transition: all 0.2s ease;
  color: #005071;

  &:hover {
    background: rgba(0, 80, 113, 0.08);
  }

  svg {
    transform: rotate(${({ isCollapsed }) => (isCollapsed ? '-90deg' : '0deg')});
    transition: transform 0.3s ease;
    font-size: 18px;
  }
`;

/* ── Scroll container ── */
const ScrollWrapper = styled.div`
  position: relative;
  display: flex;
  align-items: center;
`;

const ScrollButton = styled.button<{ direction: 'left' | 'right' }>`
  position: absolute;
  ${({ direction }) => (direction === 'left' ? 'left: -20px;' : 'right: -20px;')}
  z-index: 3;
  width: 40px;
  height: 40px;
  border-radius: 50%;
  border: none;
  background: #ffffff;
  box-shadow: 0 2px 12px rgba(0, 0, 0, 0.15);
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.2s ease;

  &:hover {
    background: #005071;
    box-shadow: 0 4px 16px rgba(0, 80, 113, 0.3);

    svg,
    span {
      color: #ffffff !important;
    }
  }

  svg,
  span {
    color: #005071 !important;
    font-size: 16px;
  }

  @media (max-width: 768px) {
    width: 34px;
    height: 34px;
    ${({ direction }) => (direction === 'left' ? 'left: -12px;' : 'right: -12px;')}
  }
`;

const ScrollContainer = styled.div`
  display: flex;
 
  gap: 26px;
 
  overflow-x: auto;
 
  scroll-behavior: smooth;
 
  padding: 12px 10px 20px 10px;
 
  align-items: stretch;
 
  scrollbar-width: none;
 
  &::-webkit-scrollbar {
    display: none;
  }
`;

const DashboardCardSlot = styled.div`
  flex: 0 0 285px;
 
  min-width: 285px;
 
  display: flex;
 
  justify-content: center;
`;

/* ── Empty state ── */
const EmptyCategory = styled.div`
  display: flex;
  align-items: center;
  justify-content: center;
  height: 140px;
  width: 100%;
  background: rgba(255, 255, 255, 0.6);
  border-radius: 12px;
  /* Removed dashed border */
  color: #999999;
  font-family: 'Poppins', sans-serif;
  font-size: 14px;
`;

/* ── Loading state ── */
const LoadingWrapper = styled.div`
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 400px;
`;

/* ══════════════════════════════════════════════════════
   ScrollableDashboardRow Component
   ══════════════════════════════════════════════════════ */
interface ScrollableDashboardRowProps {
  dashboards: DashboardItem[];
  hasPerm: (name: string) => boolean;
  userId?: string | number;
  saveFavoriteStatus: (id: number, isStarred: boolean) => void;
  favoriteStatus: Record<string, boolean>;
  onEdit: (dashboard: DashboardItem) => void;
  onDelete: (dashboard: DashboardItem) => void;
  onExport: (dashboardsToExport: DashboardItem[]) => void;
}

function ScrollableDashboardRow({
  dashboards,
  hasPerm,
  userId,
  saveFavoriteStatus,
  favoriteStatus,
  onEdit,
  onDelete,
  onExport,
}: ScrollableDashboardRowProps) {
  const scrollRef = useRef<HTMLDivElement>(null);
  const [showLeftArrow, setShowLeftArrow] = useState(false);
  const [showRightArrow, setShowRightArrow] = useState(false);

  const checkScrollPosition = useCallback(() => {
    const el = scrollRef.current;
    if (!el) return;
    setShowLeftArrow(el.scrollLeft > 10);
    setShowRightArrow(el.scrollLeft + el.clientWidth < el.scrollWidth - 10);
  }, []);

  useEffect(() => {
    checkScrollPosition();
    const el = scrollRef.current;
    if (el) {
      el.addEventListener('scroll', checkScrollPosition);
      window.addEventListener('resize', checkScrollPosition);
    }
    return () => {
      if (el) el.removeEventListener('scroll', checkScrollPosition);
      window.removeEventListener('resize', checkScrollPosition);
    };
  }, [checkScrollPosition, dashboards]);

  const scroll = (direction: 'left' | 'right') => {
    const el = scrollRef.current;
    if (!el) return;
    const scrollAmount = 340; // card width + gap
    el.scrollBy({
      left: direction === 'left' ? -scrollAmount : scrollAmount,
      behavior: 'smooth',
    });
  };

  if (dashboards.length === 0) {
    return <EmptyCategory>{t('No dashboards in this category')}</EmptyCategory>;
  }

  return (
    <ScrollWrapper>
      {showLeftArrow && (
        <ScrollButton
          direction="left"
          onClick={() => scroll('left')}
          aria-label={t('Scroll left')}
        >
          ‹
        </ScrollButton>
      )}

      <ScrollContainer ref={scrollRef}>
        {dashboards.map(dashboard => (
          <DashboardCardSlot key={dashboard.id}>
            <DashboardCard
              dashboard={dashboard}
              hasPerm={hasPerm}
              bulkSelectEnabled={false}
              showThumbnails
              userId={userId}
              loading={false}
              openDashboardEditModal={onEdit}
              saveFavoriteStatus={saveFavoriteStatus}
              favoriteStatus={favoriteStatus[String(dashboard.id)]}
              handleBulkDashboardExport={onExport}
              onDelete={onDelete}
            />
          </DashboardCardSlot>
        ))}
      </ScrollContainer>

      {showRightArrow && (
        <ScrollButton
          direction="right"
          onClick={() => scroll('right')}
          aria-label={t('Scroll right')}
        >
          ›
        </ScrollButton>
      )}
    </ScrollWrapper>
  );
}

/* ── Exports kept for backward compatibility ── */
export interface ActivityData {
  [TableTab.Created]?: JsonObject[];
  [TableTab.Edited]?: JsonObject[];
  [TableTab.Viewed]?: JsonObject[];
  [TableTab.Other]?: JsonObject[];
}

interface LoadingProps {
  cover?: boolean;
}

export const LoadingCards = ({ cover }: LoadingProps) => (
  <CardContainer showThumbnails={cover} className="loading-cards">
    {[...new Array(loadingCardCount)].map((_, index) => (
      <ListViewCard
        key={index}
        cover={cover ? false : <></>}
        description=""
        loading
      />
    ))}
  </CardContainer>
);

/* ══════════════════════════════════════════════════════
   Welcome (Home) Component
   ══════════════════════════════════════════════════════ */
interface WelcomeProps {
  user: { userId: string | number; roles?: Record<string, [string, string][]> };
  addDangerToast: (msg: string) => void;
  addSuccessToast: (msg: string) => void;
}

const DASHBOARD_LIST_PATH = '/dashboard/list/';

const PASSWORDS_NEEDED_MESSAGE = t(
  'The passwords for the databases below are needed in order to ' +
    'import them together with the dashboards. Please note that the ' +
    '"Secure Extra" and "Certificate" sections of ' +
    'the database configuration are not present in export files, and ' +
    'should be added manually after the import if they are needed.',
);
const CONFIRM_OVERWRITE_MESSAGE = t(
  'You are importing one or more dashboards that already exist. ' +
    'Overwriting might cause you to lose some of your work. Are you ' +
    'sure you want to overwrite?',
);

function Welcome({ user, addDangerToast, addSuccessToast }: WelcomeProps) {
  const history = useHistory();
  const [dashboardsByCategory, setDashboardsByCategory] = useState<
    Record<string, DashboardItem[]>
  >({});
  const [isLoading, setIsLoading] = useState(true);
  const [collapsedCategories, setCollapsedCategories] = useState<Set<string>>(
    new Set(),
  );
  const [searchValue, setSearchValue] = useState('');
  const [viewMode] = useState<'grid' | 'list'>('grid');
  const [preparingExport, setPreparingExport] = useState(false);
  const [editModal, setEditModal] = useState<DashboardItem | undefined>();
  const [dashboardToDelete, setDashboardToDelete] =
    useState<DashboardItem | null>(null);
  const [importingDashboard, showImportModal] = useState(false);
  const [passwordFields, setPasswordFields] = useState<string[]>([]);
  const [sshTunnelPasswordFields, setSSHTunnelPasswordFields] = useState<string[]>([]);
  const [sshTunnelPrivateKeyFields, setSSHTunnelPrivateKeyFields] = useState<string[]>([]);
  const [sshTunnelPrivateKeyPasswordFields, setSSHTunnelPrivateKeyPasswordFields] = useState<string[]>([]);

  const canCreate = findPermission('can_write', 'Dashboard', user?.roles);
  const canDelete = findPermission('can_write', 'Dashboard', user?.roles);
  const canExport = findPermission('can_export', 'Dashboard', user?.roles);
  const canWrite = findPermission('can_write', 'Dashboard', user?.roles);

  const fetchDashboards = useCallback(async () => {
    try {
      const queryParams = rison.encode({
        columns: [
          'id',
          'dashboard_title',
          'category',
          'url',
          'published',
          'thumbnail_url',
          'changed_on_delta_humanized',
          'changed_by',
          'owners',
        ],
        page_size: 100,
        order_column: 'changed_on',
        order_direction: 'desc',
      });

      const response = await SupersetClient.get({
        endpoint: `/api/v1/dashboard/?q=${queryParams}`,
      });

      const allDashboards: DashboardItem[] = response.json?.result || [];

      const grouped: Record<string, DashboardItem[]> = {};
      DASHBOARD_CATEGORIES.forEach(cat => {
        grouped[cat] = [];
      });

      allDashboards.forEach(d => {
        if (d.category && grouped[d.category] !== undefined) {
          grouped[d.category].push(d);
        }
      });

      setDashboardsByCategory(grouped);
    } catch (err) {
      addDangerToast(t('There was an issue fetching dashboards: %s', String(err)));
    } finally {
      setIsLoading(false);
    }
  }, [addDangerToast]);

  useEffect(() => {
    fetchDashboards();
  }, [fetchDashboards]);

  const dashboardIds = useMemo(
    () =>
      Object.values(dashboardsByCategory)
        .flat()
        .map(dashboard => dashboard.id),
    [dashboardsByCategory],
  );

  const [saveFavoriteStatus, favoriteStatus] = useFavoriteStatus(
    'dashboard',
    dashboardIds,
    addDangerToast,
  );

  const hasPerm = useCallback(
    (name: string) => {
      if (name === 'can_export') {
        return canExport;
      }
      if (name === 'can_write') {
        return canWrite;
      }
      return false;
    },
    [canExport, canWrite],
  );

  const handleBulkDashboardExport = useCallback(
    (dashboardsToExport: DashboardItem[]) => {
      const ids = dashboardsToExport.map(({ id }) => id);
      handleResourceExport('dashboard', ids, () => {
        setPreparingExport(false);
      });
      setPreparingExport(true);
    },
    [],
  );

  const handleDashboardEdit = useCallback(
    (edits: DashboardItem) =>
      SupersetClient.get({
        endpoint: `/api/v1/dashboard/${edits.id}`,
      }).then(
        () => fetchDashboards(),
        error =>
          addDangerToast(
            t('An error occurred while fetching dashboards: %s', String(error)),
          ),
      ),
    [addDangerToast, fetchDashboards],
  );

  const handleDashboardDelete = useCallback(async () => {
    if (!dashboardToDelete) {
      return;
    }
    try {
      await SupersetClient.delete({
        endpoint: `/api/v1/dashboard/${dashboardToDelete.id}`,
      });
      addSuccessToast(t('Deleted: %s', dashboardToDelete.dashboard_title));
      setDashboardsByCategory(current =>
        Object.fromEntries(
          Object.entries(current).map(([category, dashboards]) => [
            category,
            dashboards.filter(d => d.id !== dashboardToDelete.id),
          ]),
        ),
      );
    } catch (error) {
      addDangerToast(
        t(
          'There was an issue deleting %s: %s',
          dashboardToDelete.dashboard_title,
          String(error),
        ),
      );
    } finally {
      setDashboardToDelete(null);
    }
  }, [addDangerToast, addSuccessToast, dashboardToDelete]);

  const handleDashboardImport = useCallback(() => {
    showImportModal(false);
    fetchDashboards();
    addSuccessToast(t('Dashboard imported'));
  }, [addSuccessToast, fetchDashboards]);

  const toggleCategory = useCallback((category: string) => {
    setCollapsedCategories(prev => {
      const newSet = new Set(prev);
      if (newSet.has(category)) {
        newSet.delete(category);
      } else {
        newSet.add(category);
      }
      return newSet;
    });
  }, []);

  const navigateToList = useCallback(
    (viewModeParam?: 'card' | 'table') => {
      const path =
        viewModeParam !== undefined
          ? `${DASHBOARD_LIST_PATH}?viewMode=${viewModeParam}`
          : DASHBOARD_LIST_PATH;
      history.push(path);
    },
    [history],
  );

  const handleViewModeChange = useCallback(
    (mode: 'grid' | 'list') => {
      if (mode === 'list') {
        navigateToList('table');
      }
    },
    [navigateToList],
  );

  const handleHeaderDownload = useCallback(() => {
    const allDashboards = DASHBOARD_CATEGORIES.flatMap(
      category => dashboardsByCategory[category] || [],
    );
    if (allDashboards.length > 0) {
      handleBulkDashboardExport(allDashboards);
    }
  }, [dashboardsByCategory, handleBulkDashboardExport]);

  const filteredBySearch = useMemo(() => {
    if (!searchValue.trim()) return dashboardsByCategory;
    const q = searchValue.trim().toLowerCase();
    const out: Record<string, DashboardItem[]> = {};
    DASHBOARD_CATEGORIES.forEach(cat => {
      const list = dashboardsByCategory[cat] || [];
      out[cat] = list.filter(d =>
        d.dashboard_title?.toLowerCase().includes(q),
      );
    });
    return out;
  }, [dashboardsByCategory, searchValue]);

  if (isLoading) {
    return (
      <PageContainer>
        <LoadingWrapper>
          <Loading />
        </LoadingWrapper>
      </PageContainer>
    );
  }

  return (
    <PageContainer data-test="welcome-page">
      <InsightsViewHeader
        searchValue={searchValue}
        onSearchChange={setSearchValue}
        onBulkSelect={() => navigateToList()}
        // Match InsightsViews page behavior: create a new dashboard
        onAdd={() => navigateTo('/dashboard/new', { assign: true })}
        onDownload={handleHeaderDownload}
        onImport={() => showImportModal(true)}
        viewMode={viewMode}
        onViewModeChange={handleViewModeChange}
        canCreate={canCreate}
        canDelete={canDelete}
        canExport={canExport}
        showGridViewOption={false}
        showListViewOption={false}
        showDownloadOption={false}
        useDownloadIconForImport
      />

      {/* Category sections */}
      <CategoriesContainer>
        {DASHBOARD_CATEGORIES.map(category => {
          const dashboards = filteredBySearch[category] || [];
          const isCollapsed = collapsedCategories.has(category);
          return (
            <CategorySection key={category}>
              <CategoryHeader>
                <CategoryTitleWrapper>
                  <CategoryIcon>
                    {CATEGORY_ICONS[category] || (
                      <Icons.AppstoreOutlined iconSize="l" />
                    )}
                  </CategoryIcon>
                  <CategoryTitle>
                    {t(category)}
                    <CategoryCount>
                      ({dashboards.length}{' '}
                      {dashboards.length === 1
                        ? t('dashboard')
                        : t('dashboards')}
                      )
                    </CategoryCount>
                  </CategoryTitle>
                </CategoryTitleWrapper>
                <CollapseButton
                  isCollapsed={isCollapsed}
                  onClick={() => toggleCategory(category)}
                  aria-label={
                    isCollapsed
                      ? t('Expand %s', category)
                      : t('Collapse %s', category)
                  }
                >
                  <Icons.DownOutlined />
                </CollapseButton>
              </CategoryHeader>

              {!isCollapsed && (
                <ScrollableDashboardRow
                  dashboards={dashboards}
                  hasPerm={hasPerm}
                  userId={user?.userId}
                  saveFavoriteStatus={saveFavoriteStatus}
                  favoriteStatus={favoriteStatus}
                  onEdit={dashboard => setEditModal(dashboard)}
                  onDelete={dashboard => setDashboardToDelete(dashboard)}
                  onExport={handleBulkDashboardExport}
                />
              )}
            </CategorySection>
          );
        })}
      </CategoriesContainer>
      {editModal && (
        <PropertiesModal
          dashboardId={editModal.id}
          show
          onHide={() => setEditModal(undefined)}
          onSubmit={handleDashboardEdit}
        />
      )}
      {dashboardToDelete && (
        <DeleteModal
          description={
            <>
              {t('Are you sure you want to delete')}{' '}
              <b>{dashboardToDelete.dashboard_title}</b>?
            </>
          }
          onConfirm={handleDashboardDelete}
          onHide={() => setDashboardToDelete(null)}
          open={!!dashboardToDelete}
          title={t('Please confirm')}
        />
      )}
      <ImportModelsModal
        resourceName="dashboard"
        resourceLabel={t('dashboard')}
        passwordsNeededMessage={PASSWORDS_NEEDED_MESSAGE}
        confirmOverwriteMessage={CONFIRM_OVERWRITE_MESSAGE}
        addDangerToast={addDangerToast}
        addSuccessToast={addSuccessToast}
        onModelImport={handleDashboardImport}
        show={importingDashboard}
        onHide={() => showImportModal(false)}
        passwordFields={passwordFields}
        setPasswordFields={setPasswordFields}
        sshTunnelPasswordFields={sshTunnelPasswordFields}
        setSSHTunnelPasswordFields={setSSHTunnelPasswordFields}
        sshTunnelPrivateKeyFields={sshTunnelPrivateKeyFields}
        setSSHTunnelPrivateKeyFields={setSSHTunnelPrivateKeyFields}
        sshTunnelPrivateKeyPasswordFields={sshTunnelPrivateKeyPasswordFields}
        setSSHTunnelPrivateKeyPasswordFields={setSSHTunnelPrivateKeyPasswordFields}
      />
      {preparingExport && <Loading />}
    </PageContainer>
  );
}

export default withToasts(Welcome);
