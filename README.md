
/******************************************************************
* EXL SERVICE EXECUTIVE PREMIERE - FINAL UNIFIED VERSION
******************************************************************/

/* 1. THE CANVAS: Global Fixed Gradient */
html, body, #app, .dashboard, .dashboard-content, .ant-layout {
    background-color: #f0f4f8 !important;
    background-image: 
        radial-gradient(at 0% 0%, rgba(0, 82, 204, 0.08) 0px, transparent 50%), 
        radial-gradient(at 100% 0%, rgba(251, 78, 11, 0.05) 0px, transparent 50%),
        linear-gradient(180deg, #ffffff 0%, #e2e8f0 100%) !important;
    background-attachment: fixed !important;
    min-height: 100vh !important;
}

/* 2. HEADER TRANSPARENCY: Fixes the "White Header" issue */
header, 
.top-superset-navbar, 
.ant-layout-header,
#main-menu,
.nav-container {
    background: transparent !important;
    background-color: transparent !important;
    border-bottom: 1px solid rgba(203, 213, 225, 0.3) !important;
    box-shadow: none !important;
}

/* Target the specific logo/brand area */
.navbar-brand, .header-title, .ant-menu {
    background: transparent !important;
}

/* 3. CHART TITLES */
.chart-header .header-title, 
.dragdroppable-column .header-title,
.dashboard-component-chart-holder [data-test="editable-title"] button,
.dashboard-component-header span[role="button"] {
    color: #1e293b !important;
    font-weight: 700 !important;
    font-size: 15px !important;
    text-transform: capitalize;
}

/* 4. THE CARD (Glassmorphism) */
.dashboard-component-chart-holder {
    background: rgba(255, 255, 255, 0.85) !important;
    backdrop-filter: blur(8px) !important;
    border-radius: 12px !important;
    border: 1px solid rgba(203, 213, 225, 0.5) !important;
    box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.05), 0 2px 4px -1px rgba(0, 0, 0, 0.03) !important;
    padding: 12px !important;
    transition: all 0.3s ease;
    margin-bottom: 20px;
}

.dashboard-component-chart-holder:hover {
    box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1) !important;
    border: 1px solid rgba(0, 82, 204, 0.3) !important;
}

/* 5. BIG NUMBER / KPI VALUES */
.big-number-chart div, 
.dashboard-component-chart-holder div[data-test="big-number-total"],
.dashboard-component-chart-holder svg text.main-line {
    color: #2563eb !important; 
    fill: #2563eb !important;
    font-weight: 800 !important;
    font-size: 44px !important; 
    letter-spacing: -1px;
}

/* 6. TABLE UI: Super Attractive & Professional */
.superset-stylable-table-container, .ant-table-wrapper {
    background: white !important;
    border-radius: 8px;
    overflow: hidden;
    box-shadow: 0 1px 3px rgba(0,0,0,0.1);
}

.ant-table-thead > tr > th {
    background: #f8fafc !important;
    color: #475569 !important;
    font-weight: 600 !important;
    font-size: 12px !important;
    border-bottom: 2px solid #e2e8f0 !important;
    padding: 12px 16px !important;
}

.ant-table-tbody > tr > td {
    color: #1e293b !important;
    font-size: 13px !important;
    padding: 14px 16px !important;
    border-bottom: 1px solid #f1f5f9 !important;
}

.ant-table-tbody > tr.ant-table-row:nth-child(even) {
    background: #fcfdfe !important;
}

.ant-table-tbody > tr.ant-table-row:hover > td {
    background: rgba(37, 99, 235, 0.04) !important;
}

/* 7. TAB STYLING (Executive Summary, etc.) */
.nav-tabs, .ant-tabs-nav {
    background: transparent !important;
    border-bottom: 2px solid rgba(226, 232, 240, 0.5) !important;
}

.ant-tabs-tab {
    background: transparent !important;
}

.nav-tabs > li > a, .ant-tabs-tab-btn {
    font-weight: 600 !important;
    color: #64748b !important;
    border: none !important;
}

.nav-tabs > li.active > a, .ant-tabs-tab-active .ant-tabs-tab-btn {
    color: #2563eb !important;
    border-bottom: 3px solid #2563eb !important;
}
