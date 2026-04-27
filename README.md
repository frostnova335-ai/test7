/******************************************************************
* EXL SERVICE EXECUTIVE PREMIERE - REPAIRED FOR MODERN SUPERSET
******************************************************************/

/* 1. THE CANVAS */
body, #app, .dashboard, .dashboard-content {
    background-color: #ffffff !important;
    background-image: 
        radial-gradient(at 0% 0%, rgba(251, 78, 11, 0.12) 0px, transparent 50%), 
        radial-gradient(at 100% 100%, rgba(251, 78, 11, 0.05) 0px, transparent 50%),
        linear-gradient(135deg, #f8fafc 0%, #ffffff 100%) !important;
    background-attachment: fixed !important;
}

/* 2. CHART TITLES (FIXED) */
/* Targets the actual text inside the header of the chart component */
.chart-header .header-title, 
.dragdroppable-column .header-title,
.dashboard-component-chart-holder [data-test="editable-title"] button,
.dashboard-component-header span[role="button"] {
    color: #0f172a !important;
    font-weight: 800 !important;
    font-size: 16px !important;
    letter-spacing: 0.3px;
    opacity: 1 !important;
}

/* 3. THE CARD (FROSTED GLASS) */
.dashboard-component-chart-holder {
    background: rgba(255, 255, 255, 0.7) !important;
    backdrop-filter: blur(12px) saturate(150%) !important;
    -webkit-backdrop-filter: blur(12px) saturate(150%) !important;
    border-radius: 16px !important;
    border: 1px solid rgba(251, 78, 11, 0.2) !important;
    box-shadow: 0 8px 32px rgba(0, 51, 102, 0.05) !important;
    padding: 16px !important;
    transition: transform 0.2s ease-in-out;
}

.dashboard-component-chart-holder:hover {
    transform: translateY(-4px);
}

/* 4. BIG NUMBER / KPI VALUES (FIXED) */
/* Targets the actual SVG and DIV based big numbers */
.big-number-chart div, 
.dashboard-component-chart-holder .header-line,
.dashboard-component-chart-holder div[data-test="big-number-total"] {
    color: #002b5c !important;
    font-weight: 700 !important;
    font-size: 48px !important; /* Adjusted size */
}

/* Targets SVG based Big Numbers (legacy) */
.dashboard-component-chart-holder svg text.main-line {
    fill: #002b5c !important;
    font-weight: 700 !important;
    font-size: 48px !important;
}

/* 5. TABLES (FIXED) */
/* Target Ant-Design specific classes used in Superset Tables */
.superset-stylable-table-container, .ant-table-wrapper {
    background: transparent !important;
}

/* Table Headers */
.ant-table-thead > tr > th {
    background: rgba(0, 51, 102, 0.05) !important;
    color: #003366 !important;
    font-weight: 700 !important;
    text-transform: uppercase !important;
    font-size: 11px !important;
    border-bottom: 2px solid rgba(251, 78, 11, 0.2) !important;
}

/* Table Cells */
.ant-table-tbody > tr > td, 
.ant-table-row td {
    color: #334155 !important;
    font-size: 13px !important;
    background: transparent !important;
    border-bottom: 1px solid rgba(0, 51, 102, 0.05) !important;
}

/* Zebra Striping */
.ant-table-tbody > tr.ant-table-row:nth-child(even) {
    background: rgba(0, 51, 102, 0.02) !important;
}

/* Hover Effect */
.ant-table-tbody > tr.ant-table-row:hover > td {
    background: rgba(251, 78, 11, 0.08) !important;
}

/* 6. LEGENDS AND AXIS LABELS */
.nvd3 .nv-axis text, .nvd3 .nv-legend text, .recharts-text {
    fill: #475569 !important;
    font-size: 11px !important;
}
