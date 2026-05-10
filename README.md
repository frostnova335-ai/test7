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
import { useEffect, useState } from 'react';
import { useHistory } from 'react-router-dom';
import {
  isFeatureEnabled,
  FeatureFlag,
  t,
  SupersetClient,
  styled,
} from '@superset-ui/core';
import {
  Dropdown,
  FaveStar,
} from '@superset-ui/core/components';
import { MenuItem } from '@superset-ui/core/components/Menu';
import { Icons } from '@superset-ui/core/components/Icons';
import { Dashboard } from 'src/views/CRUD/types';


// Dashboard Description Mapping
const dashboardDescriptions: Record<number, string> = {
  50: 'Turn-by-turn sentiment scoring across every conversation. Generate insights around point of frustration, sentiment recovery, sentiment uplift.',
  57: 'Repeat contact detection and root cause classification. Identifies policy gaps and agent repeat contact rates across all channels.',
  3: 'Agent Productivity Insights',
  4: 'Customer Experience Metrics',
  5: 'Business Intelligence Overview',
};

const CardContainer = styled.div`
  font-family: 'Poppins', sans-serif;
 
  background: linear-gradient(
    135deg,
    #ffffff 0%,
    #dee9f5 45%,
    #c8e1fa 100%
  );
 
  border-radius: 20px;
  overflow: hidden;
  cursor: pointer;
 
  transition: transform 0.2s, box-shadow 0.2s;
 
  box-shadow: 0 6px 20px rgba(0, 0, 0, 0.12);
 
  &:hover {
    transform: translateY(-5px);
    box-shadow: 0 10px 28px rgba(0, 0, 0, 0.18);
  }
`;

const ThumbnailContainer = styled.div`
  width: 100%;
  height: 260px;
 
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
 
  padding: 30px 20px 10px 20px;
 
  img {
    width: 90px;
    height: 90px;
    object-fit: contain;
    margin-bottom: 22px;
  }
`;


const CardContent = styled.div`
  padding: 0px 18px 18px 18px;
`;

const TitleText = styled.h3`
  font-family: 'Poppins', sans-serif;
  font-size: 24px;
  font-weight: 700;
  color: #003b70;
  margin: 0;
  text-align: center;
`;

const DescriptionText = styled.p`
  color: #245b8f;
  font-size: 14px;
  margin-top: 12px;
  text-align: center;
  line-height: 22px;
`;

const TitleRow = styled.div`
  display: flex;
  align-items: flex-start;
  justify-content: space-between;
  gap: 8px;
`;

const ActionsContainer = styled.div`
  display: flex;
  align-items: center;
  gap: 10px;
`;

const BadgesContainer = styled.div`
  display: flex;
  align-items: center;
  gap: 8px;
  flex-shrink: 0;
  justify-content: flex-end;
`;

const MetaRow = styled.div`
  display: flex;
  align-items: center;
  justify-content: space-between;
 
  margin-top: 10px;
`;

const CategoryBadge = styled.span`
  font-size: 11px;
  font-weight: 500;
 
  padding: 5px 12px;
 
  border-radius: 20px;
 
  background: rgba(0, 80, 160, 0.12);
 
  color: #004f90;
 
  border: 1px solid rgba(0, 80, 160, 0.18);
`;

const IconButton = styled.button`
  background: transparent;
  border: none;
  padding: 4px;
  cursor: pointer;
 
  display: flex;
  align-items: center;
  justify-content: center;
 
  color: #004f90;
 
  border-radius: 6px;
 
  &:hover {
    background: rgba(0, 80, 160, 0.08);
  }
 
  svg {
    width: 18px;
    height: 18px;
  }
`;



const PublishedBadge = styled.span<{ isPublished: boolean }>`
  font-family: 'Poppins', sans-serif;
  font-size: 11px;
  font-weight: 500;
  padding: 4px 10px;
  border-radius: ${({ theme }) => theme.borderRadius}px;
  background: ${({ isPublished }) => (isPublished ? '#e6f7e9' : '#f5f5f5')};
  color: ${({ isPublished }) => (isPublished ? '#52c41a' : '#999999')};
  border: 1px solid ${({ isPublished }) => (isPublished ? '#b7eb8f' : '#d9d9d9')};
  white-space: nowrap;
  flex-shrink: 0;
`;

interface DashboardCardProps {
  dashboard: Dashboard;
  hasPerm: (name: string) => boolean;
  bulkSelectEnabled: boolean;
  loading: boolean;
  openDashboardEditModal?: (d: Dashboard) => void;
  saveFavoriteStatus: (id: number, isStarred: boolean) => void;
  favoriteStatus: boolean;
  userId?: string | number;
  showThumbnails?: boolean;
  handleBulkDashboardExport: (dashboardsToExport: Dashboard[]) => void;
  onDelete: (dashboard: Dashboard) => void;
}

function DashboardCard({
  dashboard,
  hasPerm,
  bulkSelectEnabled,
  userId,
  openDashboardEditModal,
  favoriteStatus,
  saveFavoriteStatus,
  showThumbnails,
  handleBulkDashboardExport,
  onDelete,
}: DashboardCardProps) {
  const history = useHistory();
  const canEdit = hasPerm('can_write');
  const canDelete = hasPerm('can_write');
  const canExport = hasPerm('can_export');
  const [thumbnailUrl, setThumbnailUrl] = useState<string | null>(null);
  const [isFetchingThumbnail, setIsFetchingThumbnail] = useState<boolean>(false);

  useEffect(() => {
    // Fetch thumbnail only if it's not already fetched
    if (
      !isFetchingThumbnail &&
      dashboard.id &&
      thumbnailUrl === null &&
      isFeatureEnabled(FeatureFlag.Thumbnails)
    ) {
      // Use existing thumbnail URL if available
      if (dashboard.thumbnail_url) {
        setThumbnailUrl(dashboard.thumbnail_url);
        return;
      }
      // Fetch thumbnail from API
      setIsFetchingThumbnail(true);
      SupersetClient.get({
        endpoint: `/api/v1/dashboard/${dashboard.id}`,
      })
        .then(({ json = {} }) => {
          setThumbnailUrl(json.result?.thumbnail_url || '');
        })
        .catch(() => {
          setThumbnailUrl('');
        })
        .finally(() => {
          setIsFetchingThumbnail(false);
        });
    }
  }, [dashboard.id, dashboard.thumbnail_url, isFetchingThumbnail, thumbnailUrl]);

  const menuItems: MenuItem[] = [];

  if (canEdit && openDashboardEditModal) {
    menuItems.push({
      key: 'edit',
      label: (
        <div
          role="button"
          tabIndex={0}
          className="action-button"
          onClick={() => openDashboardEditModal(dashboard)}
          data-test="dashboard-card-option-edit-button"
        >
          <Icons.EditOutlined iconSize="l" data-test="edit-alt" /> {t('Edit')}
        </div>
      ),
    });
  }

  if (canExport) {
    menuItems.push({
      key: 'export',
      label: (
        <div
          role="button"
          tabIndex={0}
          onClick={() => handleBulkDashboardExport([dashboard])}
          className="action-button"
          data-test="dashboard-card-option-export-button"
        >
          <Icons.UploadOutlined iconSize="l" /> {t('Export')}
        </div>
      ),
    });
  }

  if (canDelete) {
    menuItems.push({
      key: 'delete',
      label: (
        <div
          role="button"
          tabIndex={0}
          className="action-button"
          onClick={() => onDelete(dashboard)}
          data-test="dashboard-card-option-delete-button"
        >
          <Icons.DeleteOutlined iconSize="l" /> {t('Delete')}
        </div>
      ),
    });
  }

  const handleCardClick = () => {
    if (!bulkSelectEnabled) {
      history.push(dashboard.url);
    }
  };

  const dashboardDescription =
    dashboardDescriptions[dashboard.id];

  const handleActionClick = (e: React.MouseEvent) => {
    e.stopPropagation();
    e.preventDefault();
  };

  return (
    <CardContainer onClick={handleCardClick}>

      <ThumbnailContainer>

        <img
          src={`/static/images/${dashboard.id}.png`}
          alt={dashboard.dashboard_title}
          onError={(e) => {
            console.error(
              `Image not found: /static/images/${dashboard.id}.png`,
            );

            const target = e.target as HTMLImageElement;
            target.style.display = 'none';
          }}
          style={{
            width: '90px',
            height: '90px',
            objectFit: 'contain',
            marginBottom: '22px',
          }}
        />

        <TitleText>
          {dashboard.dashboard_title}
        </TitleText>

        {dashboardDescription && (
          <DescriptionText>
            {dashboardDescription}
          </DescriptionText>
        )}

      </ThumbnailContainer>

      <CardContent>

        <MetaRow>

          <ActionsContainer onClick={handleActionClick}>

            {userId && (
              <FaveStar
                itemId={dashboard.id}
                saveFaveStar={saveFavoriteStatus}
                isStarred={favoriteStatus}
              />
            )}

            <Dropdown menu={{ items: menuItems }} trigger={['hover', 'click']}>
              <IconButton type="button" aria-label="More options">
                <Icons.MoreOutlined />
              </IconButton>
            </Dropdown>

          </ActionsContainer>

          <BadgesContainer>

            {dashboard.category && (
              <CategoryBadge>
                {dashboard.category}
              </CategoryBadge>
            )}

            <PublishedBadge isPublished={dashboard.published}>
              {dashboard.published ? t('Published') : t('Draft')}
            </PublishedBadge>

          </BadgesContainer>

        </MetaRow>

      </CardContent>

    </CardContainer>
  );

}

export default DashboardCard;
