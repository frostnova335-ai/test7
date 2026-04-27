/******************************************************************
* EXL SERVICE EXECUTIVE PREMIERE - REFINED TYPOGRAPHY & GLOW BORDERS
******************************************************************/

/* 1. CHART VALUES: DEEP BLUE & REFINED WEIGHT */
.big-number-chart svg text,
.big-number-chart svg text tspan,
.dashboard-component-chart-holder svg text,
.dashboard-component-chart-holder svg text tspan,
div[data-test="big-number-total"],
.superset-key-value-chart-value,
.header-line,
.big-number {
    fill: #032c62 !important;
    color: #032c62 !important;   
    font-weight: 700 !important;  /* Reduced from 900 for a cleaner look */
    font-size: 38px !important;   
    font-family: "Inter", sans-serif !important;
}

/* 2. CHART TITLES & SUBTITLES */
/* Main Title */
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

/* Enhanced Subtitles */
.dashboard-component-chart-holder .header-line + div, 
.dashboard-component-chart-holder svg text[style*="font-size: 12px"],
.big-number-chart svg text:not(.main-line) {
    font-family: "Inter", sans-serif !important;
    font-weight: 500 !important;
    color: #64748b !important; /* Elegant Slate Blue-Grey */
    font-size: 13px !important;
    letter-spacing: 0.3px !important;
}

/* 3. FULL PAGE GRADIENT */
body, #app, .dashboard, .dashboard-content, .dashboard-header, .header-with-actions, header {
    background-color: #ffffff !important;
    background-image: 
        radial-gradient(at 100% 100%, rgba(3, 44, 98, 0.05) 0px, transparent 50%), 
        linear-gradient(180deg, #ffffff 0%, #ffffff 15%, #f1f5f9 100%) !important;
    background-attachment: fixed !important;
}

/* 4. EXECUTIVE TABLE DESIGN */
.superset-stylable-table-container,
.dashboard-component-chart-holder table {
    border-collapse: separate !important;
    border-spacing: 0 !important;
    width: 100% !important;
    border-radius: 12px !important;
    overflow: hidden !important;
}

.dashboard-component-chart-holder thead tr th,
.ant-table-thead > tr > th {
    background: linear-gradient(180deg, rgba(255,255,255,0.1) 0%, #032c62 100%) !important;
    background-color: #032c62 !important;
    color: #ffffff !important;      
    font-weight: 800 !important;
    font-size: 15px !important;     
    text-transform: none !important; 
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

.dashboard-component-chart-holder tbody tr:nth-child(even) {
    background: rgba(3, 44, 98, 0.03) !important;
}

.dashboard-component-chart-holder tbody tr:hover td {
    background: rgba(3, 44, 98, 0.06) !important; 
    color: #032c62 !important;
}

/* Status Colors */
td:contains("✅"), td:contains("Exceeding") { color: #059669 !important; }
td:contains("⚠️"), td:contains("Near Target") { color: #d97706 !important; }
td:contains("🔴"), td:contains("At Risk"), td:contains("Critical") { color: #dc2626 !important; }

/* 5. CHART CARDS: GLOW BORDERS */
.dashboard-component-chart-holder {
    background: linear-gradient(135deg, #ffffff 0%, rgba(255,255,255,0.9) 100%) !important;
    backdrop-filter: blur(20px) !important;
    border-radius: 20px !important;
    border: 2px solid transparent !important;
    background-clip: padding-box !important;
    position: relative;
    box-shadow: 0 0 0 2px #ffffff, 0 0 0 4px rgba(135, 206, 250, 0.4), 0 10px 30px rgba(3, 44, 98, 0.08) !important;
    padding: 24px !important;
    margin-bottom: 24px !important;
}

/* 6. TABS */
.ant-tabs-nav { margin-bottom: 30px !important; }
.ant-tabs-tab-active .ant-tabs-tab-btn {
    color: #032c62 !important;
    font-weight: 800 !important;
}

/* 7. SCROLLBARS */
::-webkit-scrollbar { width: 5px; height: 5px; }
::-webkit-scrollbar-thumb {
    background: rgba(3, 44, 98, 0.3);
    border-radius: 10px;
}
