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
import {
  forwardRef,
  ReactNode,
  useContext,
  useEffect,
  useLayoutEffect,
  useRef,
  useState,
} from 'react';
import {
  css,
  getExtensionsRegistry,
  QueryData,
  styled,
  SupersetTheme,
  t,
  useTheme,
} from '@superset-ui/core';
import { useUiConfig } from 'src/components/UiConfigContext';
import { isEmbedded } from 'src/dashboard/util/isEmbedded';
import { Tooltip, EditableTitle, Icons } from '@superset-ui/core/components';
import { useSelector } from 'react-redux';
import SliceHeaderControls from 'src/dashboard/components/SliceHeaderControls';
import { SliceHeaderControlsProps } from 'src/dashboard/components/SliceHeaderControls/types';
import FiltersBadge from 'src/dashboard/components/FiltersBadge';
import { RootState } from 'src/dashboard/types';
import { getSliceHeaderTooltip } from 'src/dashboard/util/getSliceHeaderTooltip';
import { DashboardPageIdContext } from 'src/dashboard/containers/DashboardPage';
import RowCountLabel from 'src/components/RowCountLabel';
import { Link } from 'react-router-dom';

const extensionsRegistry = getExtensionsRegistry();

type SliceHeaderProps = SliceHeaderControlsProps & {
  updateSliceName?: (arg0: string) => void;
  editMode?: boolean;
  annotationQuery?: object;
  annotationError?: object;
  sliceName?: string;
  filters: object;
  handleToggleFullSize: () => void;
  formData: object;
  width: number;
  height: number;
  exportPivotExcel?: (arg0: string) => void;
};

const annotationsLoading = t('Annotation layers are still loading.');
const annotationsError = t('One or more annotation layers failed loading.');
const CrossFilterIcon = styled(Icons.ApartmentOutlined)`
  ${({ theme }) => `
    cursor: default;
    color: ${theme.colorPrimary};
    line-height: 1.8;
  `}
`;

const ChartHeaderStyles = styled.div`
  ${({ theme }) => css`
    position: relative;
    font-size: ${theme.fontSizeLG}px;
    font-weight: ${theme.fontWeightStrong};
    margin-bottom: ${theme.sizeUnit}px;
    display: flex;
    max-width: 100%;
    align-items: flex-start;
    min-height: 0;

    & > .header-title {
      flex: 1 1 auto;
      min-width: 0;
      max-width: none;
      width: 100%;
      box-sizing: border-box;
      overflow: visible;
      text-overflow: clip;
      white-space: normal;
      overflow-wrap: anywhere;

      & > span.ant-tooltip-open {
        display: inline;
      }

      .title-with-filter-count {
        display: inline-flex;
        align-items: center;
        gap: ${theme.sizeUnit}px;
        white-space: nowrap;
        min-width: 0;
        max-width: 100%;
      }

      .title-with-filter-count .editable-title,
      .title-with-filter-count a {
        display: inline;
        white-space: inherit;
      }

      .title-with-filter-count .filter-counts {
        display: inline-flex;
        align-items: center;
        vertical-align: middle;
        margin-left: 0;
        margin-right: 0;
        padding-left: 0;
        padding-right: 0;
        background: transparent;
        border-radius: 0;
        flex: 0 0 auto;
      }

      .title-with-filter-count .filter-counts .anticon {
        display: none;
      }

      .title-with-filter-count .filter-counts .ant-badge-count {
        margin: 0;
        padding: 0;
        min-width: auto;
        height: auto;
        line-height: inherit;
        font-size: ${Math.max(theme.fontSizeSM - 1, 10)}px;
        font-weight: ${theme.fontWeightStrong};
        color: ${theme.colorPrimary};
        background: transparent;
        box-shadow: none;
        border: 0;
      }

      .title-inline-warning {
        display: inline-flex;
        vertical-align: middle;
        margin-left: ${theme.sizeUnit}px;
      }
    }

    &[data-table-viz='true'] > .header-title {
      overflow-wrap: normal;
      word-break: normal;
      white-space: nowrap;
      padding-right: clamp(110px, 28vw, 220px);
    }

    &[data-table-viz='true'][data-table-small='true'] > .header-title {
      padding-right: clamp(52px, 16vw, 90px);
    }

    &[data-kpi-viz='true'] > .header-title .editable-title,
    &[data-kpi-viz='true'] > .header-title a {
      display: block;
      width: 100%;
      max-width: 100%;
      box-sizing: border-box;
      padding-left: 0;
      margin-left: 0;
      text-indent: 0;
      white-space: normal;
      overflow-wrap: anywhere;
      word-break: normal;
    }

    &[data-table-viz='true'] > .header-title .editable-title,
    &[data-table-viz='true'] > .header-title a {
      display: inline;
      max-width: none;
      overflow: visible;
      text-overflow: clip;
      white-space: nowrap;
      overflow-wrap: normal;
      word-break: normal;
      hyphens: none;
    }

    & > .header-controls {
      display: flex;
      align-items: center;
      height: 24px;
      flex: 0 0 auto;
      min-width: max-content;
      white-space: nowrap;
      margin-left: ${theme.sizeUnit}px;
    }

    &[data-table-viz='true'] > .header-controls {
      position: absolute;
      top: 0;
      right: 0;
      z-index: 1;
    }

    .dropdown.btn-group {
      pointer-events: none;
      vertical-align: top;
      & > * {
        pointer-events: auto;
      }
    }

    .dropdown-toggle.btn.btn-default {
      background: none;
      border: none;
      box-shadow: none;
    }

    .dropdown-menu.dropdown-menu-right {
      top: ${theme.sizeUnit * 5}px;
    }

    .divider {
      margin: ${theme.sizeUnit}px 0;
    }

    .refresh-tooltip {
      display: block;
      height: ${theme.sizeUnit * 4}px;
      margin: ${theme.sizeUnit}px 0;
      color: ${theme.colorTextLabel};
    }
  `}
`;

const SliceHeader = forwardRef<HTMLDivElement, SliceHeaderProps>(
  (
    {
      forceRefresh = () => ({}),
      updateSliceName = () => ({}),
      toggleExpandSlice = () => ({}),
      logExploreChart = () => ({}),
      logEvent,
      exportCSV = () => ({}),
      exportXLSX = () => ({}),
      editMode = false,
      annotationQuery = {},
      annotationError = {},
      cachedDttm = null,
      updatedDttm = null,
      isCached = [],
      isExpanded = false,
      sliceName = '',
      supersetCanExplore = false,
      supersetCanShare = false,
      supersetCanCSV = false,
      exportPivotCSV,
      exportFullCSV,
      exportFullXLSX,
      slice,
      componentId,
      dashboardId,
      addSuccessToast,
      addDangerToast,
      handleToggleFullSize,
      isFullSize,
      chartStatus,
      formData,
      width,
      height,
      exportPivotExcel = () => ({}),
    },
    ref,
  ) => {
    const SliceHeaderExtension = extensionsRegistry.get(
      'dashboard.slice.header',
    );
    const uiConfig = useUiConfig();
    const shouldShowRowLimitWarning =
      !isEmbedded() || uiConfig.showRowLimitWarning;
    const dashboardPageId = useContext(DashboardPageIdContext);
    const [headerTooltip, setHeaderTooltip] = useState<ReactNode | null>(null);
    const headerRef = useRef<HTMLDivElement>(null);
    const titleContentRef = useRef<HTMLDivElement>(null);
    const [isTitleWrapped, setIsTitleWrapped] = useState(false);
    // TODO: change to indicator field after it will be implemented
    const crossFilterValue = useSelector<RootState, any>(
      state => state.dataMask[slice?.slice_id]?.filterState?.value,
    );
    const isCrossFiltersEnabled = useSelector<RootState, boolean>(
      ({ dashboardInfo }) => dashboardInfo.crossFiltersEnabled,
    );

    const firstQueryResponse = useSelector<RootState, QueryData | undefined>(
      state => state.charts[slice.slice_id].queriesResponse?.[0],
    );

    const theme = useTheme();

    const rowLimit = Number(formData.row_limit || -1);
    const sqlRowCount = Number(firstQueryResponse?.sql_rowcount || 0);
    const hasRowLimitWarning =
      shouldShowRowLimitWarning && sqlRowCount === rowLimit;

    const canExplore = !editMode && supersetCanExplore;
    const showFilterCountInTitle = !uiConfig.hideChartControls;
    const vizType = (slice.viz_type || '').toLowerCase();
    const isTableViz = vizType.includes('table');
    const isKpiViz = vizType.includes('big_number');
    const isSmallTableCard = isTableViz && width <= 320;
    const displaySliceName =
      typeof sliceName === 'string' ? sliceName.trim() : sliceName;

    useEffect(() => {
      const headerElement = headerRef.current;
      if (canExplore) {
        setHeaderTooltip(getSliceHeaderTooltip(displaySliceName));
      } else if (
        headerElement &&
        (headerElement.scrollWidth > headerElement.offsetWidth ||
          headerElement.scrollHeight > headerElement.offsetHeight)
      ) {
        setHeaderTooltip(displaySliceName ?? null);
      } else {
        setHeaderTooltip(null);
      }
    }, [displaySliceName, width, height, canExplore]);

    useLayoutEffect(() => {
      const titleElement = titleContentRef.current;
      if (!titleElement) {
        setIsTitleWrapped(false);
        return;
      }
      // Detect title wrap/overflow so warning icon can be moved out of text flow.
      const wrapped =
        titleElement.scrollWidth > titleElement.clientWidth ||
        titleElement.scrollHeight > titleElement.clientHeight + 1;
      setIsTitleWrapped(wrapped);
    }, [displaySliceName, width, height, showFilterCountInTitle]);

    const exploreUrl = `/explore/?dashboard_page_id=${dashboardPageId}&slice_id=${slice.slice_id}`;

    const renderExploreLink = (title: string) => (
      <Link
        to={exploreUrl}
        css={(theme: SupersetTheme) => css`
          color: ${theme.colorText};
          text-decoration: none;
          :hover {
            text-decoration: underline;
          }
          display: inline;
          white-space: normal;
          overflow-wrap: anywhere;
        `}
      >
        {title}
      </Link>
    );

    return (
      <ChartHeaderStyles
        data-test="slice-header"
        data-view-mode={!editMode ? 'true' : undefined}
        data-table-viz={
          !editMode && isTableViz ? 'true' : undefined
        }
        data-table-small={
          !editMode && isSmallTableCard ? 'true' : undefined
        }
        data-kpi-viz={!editMode && isKpiViz ? 'true' : undefined}
        ref={ref}
      >
        <div className="header-title" ref={headerRef}>
          <Tooltip title={headerTooltip}>
            {/* this div ensures the hover event triggers correctly and prevents flickering */}
            <div
              className={showFilterCountInTitle ? 'title-with-filter-count' : ''}
              ref={titleContentRef}
            >
              <EditableTitle
                title={
                  displaySliceName ||
                  (editMode
                    ? '---' // this makes an empty title clickable
                    : '')
                }
                canEdit={editMode}
                onSaveTitle={updateSliceName}
                showTooltip={false}
                renderLink={
                  canExplore && exploreUrl ? renderExploreLink : undefined
                }
              />
              {showFilterCountInTitle && (
                <FiltersBadge chartId={slice.slice_id} />
              )}
              {isSmallTableCard && hasRowLimitWarning && !isTitleWrapped && (
                <span className="title-inline-warning">
                  <RowCountLabel
                    rowcount={sqlRowCount}
                    limit={rowLimit}
                    label={
                      <Icons.WarningOutlined
                        iconSize="m"
                        iconColor={theme.colorWarning}
                      />
                    }
                  />
                </span>
              )}
            </div>
          </Tooltip>
          {!isTableViz && !!Object.values(annotationQuery).length && (
            <Tooltip
              id="annotations-loading-tooltip"
              placement="top"
              title={annotationsLoading}
            >
              <Icons.ReloadOutlined
                className="warning"
                aria-label={annotationsLoading}
              />
            </Tooltip>
          )}
          {!isTableViz && !!Object.values(annotationError).length && (
            <Tooltip
              id="annotation-errors-tooltip"
              placement="top"
              title={annotationsError}
            >
              <Icons.ExclamationCircleOutlined
                className="danger"
                aria-label={annotationsError}
              />
            </Tooltip>
          )}
        </div>
        <div className="header-controls">
          {!editMode && (
            <>
              {SliceHeaderExtension && (
                <SliceHeaderExtension
                  sliceId={slice.slice_id}
                  dashboardId={dashboardId}
                />
              )}
              {crossFilterValue && (
                <Tooltip
                  placement="top"
                  title={t(
                    'This chart applies cross-filters to charts whose datasets contain columns with the same name.',
                  )}
                >
                  <CrossFilterIcon iconSize="m" />
                </Tooltip>
              )}

              {hasRowLimitWarning && (!isSmallTableCard || isTitleWrapped) && (
                <RowCountLabel
                  rowcount={sqlRowCount}
                  limit={rowLimit}
                  label={
                    <Icons.WarningOutlined
                      iconSize={isSmallTableCard ? 'm' : 'l'}
                      iconColor={theme.colorWarning}
                      css={theme => css`
                        padding: ${isSmallTableCard ? 0 : theme.sizeUnit}px;
                      `}
                    />
                  }
                />
              )}
              {isTableViz && !!Object.values(annotationQuery).length && (
                <Tooltip
                  id="annotations-loading-tooltip-controls"
                  placement="top"
                  title={annotationsLoading}
                >
                  <Icons.ReloadOutlined
                    className="warning"
                    aria-label={annotationsLoading}
                  />
                </Tooltip>
              )}
              {isTableViz && !!Object.values(annotationError).length && (
                <Tooltip
                  id="annotation-errors-tooltip-controls"
                  placement="top"
                  title={annotationsError}
                >
                  <Icons.ExclamationCircleOutlined
                    className="danger"
                    aria-label={annotationsError}
                  />
                </Tooltip>
              )}
              {!uiConfig.hideChartControls && (
                <SliceHeaderControls
                  slice={slice}
                  isCached={isCached}
                  isExpanded={isExpanded}
                  cachedDttm={cachedDttm}
                  updatedDttm={updatedDttm}
                  toggleExpandSlice={toggleExpandSlice}
                  forceRefresh={forceRefresh}
                  logExploreChart={logExploreChart}
                  logEvent={logEvent}
                  exportCSV={exportCSV}
                  exportPivotCSV={exportPivotCSV}
                  exportFullCSV={exportFullCSV}
                  exportXLSX={exportXLSX}
                  exportFullXLSX={exportFullXLSX}
                  supersetCanExplore={supersetCanExplore}
                  supersetCanShare={supersetCanShare}
                  supersetCanCSV={supersetCanCSV}
                  componentId={componentId}
                  dashboardId={dashboardId}
                  addSuccessToast={addSuccessToast}
                  addDangerToast={addDangerToast}
                  handleToggleFullSize={handleToggleFullSize}
                  isFullSize={isFullSize}
                  isDescriptionExpanded={isExpanded}
                  chartStatus={chartStatus}
                  formData={formData}
                  exploreUrl={exploreUrl}
                  crossFiltersEnabled={isCrossFiltersEnabled}
                  exportPivotExcel={exportPivotExcel}
                />
              )}
            </>
          )}
        </div>
      </ChartHeaderStyles>
    );
  },
);

export default SliceHeader;
