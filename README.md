/******************************************************************

* EXL SERVICE EXECUTIVE PREMIERE - LIGHT GLASS ON ORANGE MESH

******************************************************************/
 
/* 1. THE CANVAS: Orange & White Mesh Gradient */

body, .dashboard, .dashboard-content {

    background-color: #ffffff !important;

    background-image: 

        radial-gradient(at 0% 0%, rgba(251, 78, 11, 0.12) 0px, transparent 50%), 

        radial-gradient(at 100% 100%, rgba(251, 78, 11, 0.05) 0px, transparent 50%),

        linear-gradient(135deg, #f8fafc 0%, #ffffff 100%) !important;

    background-attachment: fixed !important;

    font-family: 'Inter', -apple-system, sans-serif !important;

}
 
/* 2. GLOBAL TEXT COLOR */

.dashboard-header, .header-title {

    color: #003366 !important; 

}
 
/* 3. THE CARD: Light "Frosted" Glass */

.dashboard-component-chart-holder, 

.dashboard-component-markdown {

    background: rgba(255, 255, 255, 0.7) !important;

    backdrop-filter: blur(12px) saturate(150%) !important;

    -webkit-backdrop-filter: blur(12px) saturate(150%) !important;

    border-radius: 16px !important;

    border: 1px solid rgba(251, 78, 11, 0.2) !important;

    box-shadow: 0 8px 32px rgba(0, 51, 102, 0.05) !important;

    padding: 24px !important;

    margin-bottom: 20px !important;

    transition: all 0.25s ease; /* ✅ added */
}

/* ✅ Card hover enhancement */
.dashboard-component-chart-holder:hover {
    transform: translateY(-2px);
    box-shadow: 0 12px 40px rgba(0, 51, 102, 0.08) !important;
}
 
/* 4. CHART VALUES */

.dashboard-component-chart-holder text,

.dashboard-component-chart-holder tspan,

.nvd3 text,

.recharts-text,

.ace_content,

.nvd3 .nv-legend text,

.recharts-legend-item-text {

    fill: #003366 !important;

    color: #003366 !important;

    font-family: 'Inter', sans-serif !important;

}
 
/* 5. KPI & BIG NUMBERS (UPDATED) */

.big-number, 

.bigNumber, 

.dashboard-markdown h1,

.dashboard-component-chart-holder [class*="big-number"],

.dashboard-component-chart-holder [class*="BigNumber"] {

    color: #002b5c !important; /* ✅ darker blue */

    fill: #002b5c !important;

    font-weight: 700 !important; /* ✅ cleaner bold */

    font-size: 40px !important; /* ✅ slightly smaller */

    letter-spacing: -0.5px;

    text-shadow: none !important;

}

/* 6. TABLES BASE */

.ant-table, 

.table-condensed,

.ant-table-tbody > tr > td,

.ant-table-thead > tr > th,

.reactable .rt-td,

.reactable .rt-th {

    color: #003366 !important;

    background: transparent !important;

    border-bottom: 1px solid rgba(0, 51, 102, 0.08) !important;

}
 
/* ✅ TABLE HEADER IMPROVED */
.ant-table-thead > tr > th {

    font-weight: 700 !important;

    background: rgba(0, 51, 102, 0.04) !important;

    text-transform: uppercase;

    font-size: 12px !important;

    letter-spacing: 0.6px;

    padding: 10px !important;

    color: #1e293b !important;

    border-bottom: 2px solid rgba(0, 51, 102, 0.1) !important;

}
 
/* ✅ TABLE BODY IMPROVED */
.ant-table-tbody > tr > td {

    font-size: 13px !important;

    color: #334155 !important;

    padding: 10px !important;

    vertical-align: middle !important;

}

/* ✅ zebra rows */
.ant-table-tbody > tr:nth-child(even) {
    background: rgba(0, 51, 102, 0.02) !important;
}

/* ✅ hover effect */
.ant-table-tbody > tr:hover > td {
    background: rgba(251, 78, 11, 0.06) !important;
    transition: 0.2s ease;
}

/* ✅ remove hard borders */
.ant-table-tbody > tr > td,
.ant-table-thead > tr > th {
    border: none !important;
}

/* ✅ table container polish */
.ant-table {
    border-radius: 12px !important;
    overflow: hidden !important;
}
 
/* 7. AXIS & GRID LINES */

.nvd3 .nv-axis path,

.nvd3 .nv-axis line,

.recharts-cartesian-grid-horizontal line,

.recharts-cartesian-grid-vertical line {

    stroke: rgba(0, 51, 102, 0.1) !important;

}
 
/* 8. LABELS & SUB-TEXT (UPDATED TITLES) */

.chart-header .header-title,
.dashboard-component-header .header-title,
.slice_header .header-title {

    color: #0f172a !important; /* ✅ darker */

    font-weight: 700 !important; /* ✅ bold */

    font-size: 14px !important; /* ✅ bigger */

    text-transform: none !important;

    letter-spacing: 0.3px;

}

/* ✅ subtle divider under title */
.chart-header {
    border-bottom: 1px solid rgba(0, 51, 102, 0.08);
    padding-bottom: 8px;
    margin-bottom: 10px;
}

.dashboard-markdown p {

    color: #fb4e0b !important;

    font-weight: 600 !important;

    text-transform: uppercase !important;

    letter-spacing: 0.8px;

}
 
/* 9. FILTER PANEL */

.dashboard-filters-panel {

    background: rgba(255, 255, 255, 0.5) !important;

    backdrop-filter: blur(20px) !important;

    border-right: 1px solid rgba(251, 78, 11, 0.1) !important;

}

/* ✅ ICON ALIGNMENT + COLORS */
.ant-table-tbody td span,
.ant-table-tbody td svg {

    display: inline-flex;
    align-items: center;
    gap: 6px;
}

/* status colors */
.anticon-check-circle {
    color: #22c55e !important;
}

.anticon-warning {
    color: #f59e0b !important;
}

.anticon-close-circle {
    color: #ef4444 !important;
}
