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
  23: 'Turn-by-turn sentiment scoring across every conversation. Generate insights around point of frustration, sentiment recovery, sentiment uplift.',
  43: 'Repeat contact detection and root cause classification. Identifies policy gaps and agent repeat contact rates across all channels.',
  42: 'Analyze CSAT and NPS for 100 % of contacts. Identify the root cause behind the low CSAT and NPS backed by evidences.',
  3:  'Spot behavioral risks early, prioritize interventions, and help every agent perform at their best.',
  36: 'Monitor performance, track progress, achieve goals, improve strengths, enhance key metrics, and support continuous personal growth every single day.',
  20: 'Track virtual agent performance, analyze conversations and resolution rates, identify trends, and optimize automation for improved customer experiences.',
  26: 'Identify impactful automation opportunities to streamline complex processes, reduce effort, boost efficiency, and maximize overall operational performance and outcomes.',
  25: 'Gain real-time visibility into critical contact center operational metrics and performance trends.',
  24: 'Identify bottlenecks early, optimize workforce efficiency, and keep operations running at peak performance.',
  40: 'Monitor customer churn trends, identify high-risk segments, and root causes of churn, enabling proactive retention strategies and operational improvements.'
};


const CardContainer = styled.div`
  font-family: 'Poppins', sans-serif;
 
  width: 285px;
  height: 300px;
 
  background: linear-gradient(
    180deg,
    #ffffff 0%,
    #ffffff 55%,
    #f6f9fd 100%
  );
 
  border-radius: 18px;
 
  cursor: pointer;
 
  transition: all 0.25s ease;
 
  box-shadow: 0 7px 20px rgba(7, 16, 35, 0.12);
 
  position: relative;
 
  display: flex;
  flex-direction: column;
 
  overflow: hidden;
 
  padding-bottom: 14px;
 
  /* Thin top blue line */
  &::before {
    content: '';
    position: absolute;
 
    top: 0;
    left: 18px;
    right: 18px;
 
    height: 0.75px;
 
    background: linear-gradient(
      90deg,
      rgba(81, 145, 205, 0.35) 0%,
      rgba(0, 79, 112, 0.95) 100%
    );
 
    border-radius: 20px;
  }
 
  &:hover {
    transform: translateY(-5px);
 
    box-shadow: 0 14px 28px rgba(8, 16, 35, 0.14);
  }
`;


const ThumbnailContainer = styled.div`
  display: flex;
  flex-direction: column;
 
  flex: 1;
 
  padding: 18px 18px 0 18px;
 
  img {
    width: 34px;
    height: 34px;
 
    object-fit: contain;
 
    margin-bottom: 22px;
 
    align-self: flex-start;
  }
`;

const TitleText = styled.h3`
  font-family: 'Poppins', sans-serif;
 
  font-size: 16px;
  font-weight: 700;
  color: #163b63;
 
  text-align: left;
 
  margin: 0;
 
  line-height: 1.4;
 
  width: 100%;
`;

const DescriptionText = styled.p`
  color: #66788a;
 
  font-size: 11px;
 
  font-style: italic;
 
  line-height: 1.6;
 
  text-align: left;
 
  margin-top: 12px;
 
  width: 100%;
 
  min-height: 68px;
 
  margin-bottom: 0;
`;







const CardContent = styled.div`
  margin-top: auto;
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
  svg{
  color: #f26a21
  }
`;

const BadgesContainer = styled.div`
  display: flex;
  align-items: center;
  gap: 8px;
  flex-shrink: 0;
  justify-content: flex-end;
`;

const OpenButton = styled.div`
  width: 100%;
 
  display: flex;
  align-items: center;
  justify-content: flex-end;
 
  margin-top: auto;
 
  padding-top: 14px;
 
  font-size: 16px;
  font-weight: 700;
 
  color: #163b63;
 
  cursor: pointer;
 
  span {
    margin-left: 10px;
 
    color: #f26a21;
 
    font-size: 18px;
 
    line-height: 1;
  }
`;

const MetaRow = styled.div`
  display: flex;
  align-items: center;
  justify-content: space-between;
 
  padding: 12px 14px 14px 14px;
 
  margin-top: auto;
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



const CategoryBadge = styled.span`
  font-size: 11px;
  font-weight: 650;
  letter-spacing: 0.2px;
  padding: 5px 11px;
 
  border-radius: 20px;
 
  background: linear-gradient(
    135deg,
    rgb(0, 80, 113) 0%,
    rgb(81, 145, 205) 100%
  );
 
  color: #ffffff;
 
  border: none;
 
  white-space: nowrap;
 
  max-width: 170px;
 
  overflow: hidden;
 
  text-overflow: ellipsis;
 
  display: inline-block;
`;


// const PublishedBadge = styled.span<{ isPublished?: boolean }>`
//   font-family: 'Poppins', sans-serif;

//   font-size: 9px;
//   font-weight: 600;

//   padding: 4px 10px;

//   border-radius: 20px;

//   background: ${({ isPublished }) =>
//     isPublished ? '#eef2f6' : '#f4f4f4'};

//   color: ${({ isPublished }) =>
//     isPublished ? '#5f6b7a' : '#999999'};

//   border: 1px solid #dde5ee;

//   white-space: nowrap;
// `;

const StatusImage = styled.img`
  height: 22px;
  width: auto;
 
  object-fit: contain;
 
  border-radius: 6px;
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
    dashboardDescriptions[dashboard.id] ||
    'AI powered analytics and actionable insights to track and optimize performance.';

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
            const target = e.target as HTMLImageElement;

            target.src = '/static/images/default.png';
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
        <OpenButton>
          Open
          <span>➜</span>
        </OpenButton>
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

            <StatusImage
              src={
                dashboard.published
                  ? '/static/images/published.png'
                  : '/static/images/draft.png'
              }
              alt={dashboard.published ? 'Published' : 'Draft'}
            />

          </BadgesContainer>

        </MetaRow>

      </CardContent>

    </CardContainer>
  );

}

export default DashboardCard;
