/**********************
* EXL SERVICE EXECUTIVE PREMIERE — FINAL STABLE VERSION
* 
* Section 10 UPDATED: Specific fix for the Rural Breakdown 
* Pie Chart using the exact ID class (.dashboard-chart-id-104)
**********************/


/* 1. BIG NUMBER / KPI VALUES ONLY */

[data-test="big-number-total"] {
    fill: #032c62 !important;
    color: #032c62 !important;
    font-weight: 380 !important;
    font-size: 33px !important;
    font-family: "Inter", sans-serif !important;
}

.big-number .header-line,
.superset-key-value-chart-value {
    color: #032c62 !important;
    font-weight: 380 !important;
    font-size: 33px !important;
    font-family: "Inter", sans-serif !important;
}

svg.superset-svg-big-number text.main-line {
    fill: #032c62 !important;
    font-weight: 380 !important;
    font-size: 33px !important;
    font-family: "Inter", sans-serif !important;
}


/* 2. LEGEND TEXT — TARGETED, NO LAYOUT BREAKING */

.nv-legend-text {
    fill: #334155 !important;
    color: #334155 !important;
    font-size: 12px !important;
    font-weight: 600 !important;
    visibility: visible !important;
    opacity: 1 !important;
}

.dashboard-component-chart-holder .nv-legendWrap,
.dashboard-component-chart-holder svg g.nvd3.nv-legend {
    visibility: visible !important;
    opacity: 1 !important;
}

.echarts-legend-text,
.legend-item-name,
.legend-item-label {
    color: #334155 !important;
    font-size: 12px !important;
    font-weight: 600 !important;
    visibility: visible !important;
    opacity: 1 !important;
}

.echarts-for-react svg text.legend-text {
    fill: #334155 !important;
}


/* 3. CHART TITLES & SUBTITLES */

.header-title,
.dashboard-component-header span[role="button"],
.dragdroppable-column .header-title,
.editable-title span,
[data-test="editable-title"] button {
    font-weight: 700 !important;
    color: #032c62 !important;
    font-size: 16px !important;
    text-transform: none !important;
}

.dashboard-component-chart-holder .header-line + div {
    font-family: "Inter", sans-serif !important;
    font-weight: 500 !important;
    color: #64748b !important;
    font-size: 13px !important;
    letter-spacing: 0.2px !important;
}

.big-number-chart svg text:not(.main-line) {
    font-family: "Inter", sans-serif !important;
    fill: #64748b !important;
    font-weight: 500 !important;
    font-size: 13px !important;
}


/* 4. FULL PAGE GRADIENT */

body, #app, .dashboard, .dashboard-content,
.dashboard-header, .header-with-actions, header {
    background-color: #ffffff !important;
    background-image:
        radial-gradient(at 100% 100%, rgba(3, 44, 98, 0.05) 0px, transparent 50%),
        linear-gradient(180deg, #ffffff 0%, #ffffff 15%, #f1f5f9 100%) !important;
    background-attachment: fixed !important;
}


/* 5. EXECUTIVE TABLE DESIGN */

.superset-stylable-table-container,
.dashboard-component-chart-holder table {
    border-collapse: separate !important;
    border-spacing: 0 !important;
    width: 100% !important;
    border-radius: 12px !important;
}

.dashboard-component-chart-holder thead tr th,
.ant-table-thead > tr > th {
    background: linear-gradient(180deg, rgba(255,255,255,0.1) 0%, #032c62 100%) !important;
    background-color: #032c62 !important;
    color: #ffffff !important;
    font-weight: 800 !important;
    font-size: 15px !important;
    padding: 22px 15px !important;
    border: none !important;
}

.dashboard-component-chart-holder tbody tr td,
.ant-table-tbody > tr > td {
    font-weight: 700 !important;
    color: #1e293b !important;
    padding: 14px 15px !important;
    font-size: 14px !important;
    border-bottom: 1px solid #e2e8f0 !important;
}


/* 6. CHART CARDS — GLOW BORDERS */

.dashboard-component-chart-holder {
    background: linear-gradient(135deg, #ffffff 0%, rgba(255,255,255,0.9) 100%) !important;
    backdrop-filter: blur(20px) !important;
    border-radius: 20px !important;
    border: 2px solid transparent !important;
    background-clip: padding-box !important;
    box-shadow:
        0 0 0 2px #ffffff,
        0 0 0 4px rgba(135, 206, 250, 0.4),
        0 10px 30px rgba(3, 44, 98, 0.08) !important;
    padding: 24px !important;
    margin-bottom: 24px !important;
    overflow: visible !important;
}


/* 7. TOP TABS & SCROLLBARS */

.ant-tabs-nav {
    margin-bottom: 30px !important;
}

.ant-tabs-tab-active .ant-tabs-tab-btn {
    color: #032c62 !important;
    font-weight: 800 !important;
}

::-webkit-scrollbar { width: 5px; height: 5px; }

::-webkit-scrollbar-thumb {
    background: rgba(3, 44, 98, 0.3);
    border-radius: 10px;
}


/* 8. FIX: ECharts Controls & Toolbox */

.dashboard-component-chart-holder .chart-container .action-button,
.dashboard-component-chart-holder .header .dropdown-toggle {
    color: #94a3b8 !important;
    opacity: 1 !important;
    visibility: visible !important;
}

.echarts-for-react .echarts-tooltip,
.echarts-for-react .echarts-toolbar {
    color: initial !important;
    fill: initial !important;
}


/* 9. FIX: Bottom Navigation / Tabs */

.dashboard-component-tabs .ant-tabs-tab,
.dashboard-content .ant-tabs-nav .ant-tabs-tab {
    color: #475569 !important;
    font-weight: 500 !important;
}

.dashboard-component-tabs .ant-tabs-tab-active .ant-tabs-tab-btn,
.dashboard-content .ant-tabs-nav .ant-tabs-tab-active .ant-tabs-tab-btn {
    color: #032c62 !important;
    font-weight: 800 !important;
}

.dashboard-component-tabs .ant-tabs-ink-bar {
    background: #032c62 !important;
}

.dashboard-component-tabs .ant-tabs-nav {
    background: rgba(255,255,255,0.85) !important;
    border-top: 1px solid #e2e8f0 !important;
    padding-top: 10px !important;
}


//* =====================================================
   10. TARGETED FIX: RURAL BREAKDOWN PIE CHART (ID 104)
   - REMOVED padding (which broke the grid height)
   - ADDED transform to safely shift the chart up & right
   - ADDED overflow:visible to all inner containers
   ===================================================== */

/* Ensure none of the inner containers are clipping the labels */
.dashboard-chart-id-104,
.dashboard-chart-id-104 .dashboard-component-chart-holder,
.dashboard-chart-id-104 .slice_container,
.dashboard-chart-id-104 .chart-container {
    overflow: visible !important;
}

/* Shift the pie chart visual up and right using transform. 
   This is much safer than "position: relative" or "padding" 
   because it doesn't change the grid layout size. */
.dashboard-chart-id-104 .chart-container {
    transform: translate(10px, -8px) !important;
}
   ===================================================== */

/* Increase padding to prevent label truncation */
.dashboard-chart-id-104 {
    padding-right: 48px !important;
    padding-bottom: 40px !important;
}

/* Adjust the internal container positioning */
.dashboard-chart-id-104 .chart-container {
    position: relative !important;
    left: 10px !important;
    top: -8px !important;
}
