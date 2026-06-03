/**********************
* EXL SERVICE EXECUTIVE PREMIERE — FIX FOR IMAGE 1 & IMAGE 2
* 
* Image 1 Fix: Removed "display: block" on ECharts divs and removed 
*              global span/svg color overrides that broke the controls.
*
* Image 2 Fix: Added explicit color rules for the bottom dashboard 
*              navigation/tabs, which became invisible on the white bg.
**********************/


/* 1. BIG NUMBER / KPI VALUES ONLY */
/* Removed the broad "svg text" and "echarts span" rules that 
   made Image 1's toolbox text invisible on dark backgrounds */

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
/* REMOVED: The ".echarts-chart div { display: block }" that broke 
   Image 1's ECharts controls. Only target actual text nodes now. */

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


/* =====================================================
   8. FIX FOR IMAGE 1: ECharts Controls & Toolbox
   - Prevents CSS from bleeding into ECharts internal
     tooltips, axis labels, and top-right controls.
   ===================================================== */

.dashboard-component-chart-holder .chart-container .action-button,
.dashboard-component-chart-holder .header .dropdown-toggle {
    color: #94a3b8 !important; 
    opacity: 1 !important;
    visibility: visible !important;
}

/* Ensures ECharts toolbox/tooltip text uses its default theme 
   instead of being forced to deep blue (which made it invisible) */
.echarts-for-react .echarts-tooltip,
.echarts-for-react .echarts-toolbar {
    color: initial !important;
    fill: initial !important;
}


/* =====================================================
   9. FIX FOR IMAGE 2: Bottom Navigation / Tabs
   - Explicitly colors the bottom tab text, which became
     invisible when the background was forced to white.
   ===================================================== */

.dashboard-component-tabs .ant-tabs-tab,
.dashboard-content .ant-tabs-nav .ant-tabs-tab {
    color: #475569 !important; /* Visible dark slate text */
    font-weight: 500 !important;
}

.dashboard-component-tabs .ant-tabs-tab-active .ant-tabs-tab-btn,
.dashboard-content .ant-tabs-nav .ant-tabs-tab-active .ant-tabs-tab-btn {
    color: #032c62 !important; /* Deep blue active state */
    font-weight: 800 !important;
}

.dashboard-component-tabs .ant-tabs-ink-bar {
    background: #032c62 !important;
}

/* Adds a subtle light background to the bottom tabs so they 
   don't blend completely into the white page gradient */
.dashboard-component-tabs .ant-tabs-nav {
    background: rgba(255,255,255,0.85) !important;
    border-top: 1px solid #e2e8f0 !important;
    padding-top: 10px !important;
}
