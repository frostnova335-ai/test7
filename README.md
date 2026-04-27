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

    background: rgba(255, 255, 255, 0.7) !important; /* Semi-transparent White */

    backdrop-filter: blur(12px) saturate(150%) !important;

    -webkit-backdrop-filter: blur(12px) saturate(150%) !important;

    border-radius: 16px !important;

    /* Subtle Mixed Orange Border */

    border: 1px solid rgba(251, 78, 11, 0.2) !important;

    /* Soft Elevation Shadow */

    box-shadow: 0 8px 32px rgba(0, 51, 102, 0.05) !important;

    padding: 24px !important;

    margin-bottom: 20px !important;

}
 
/* 4. CHART VALUES: Forcing Data to EXL Navy */

.dashboard-component-chart-holder text,

.dashboard-component-chart-holder tspan,

.nvd3 text,

.recharts-text,

.ace_content,

.nvd3 .nv-legend text,

.recharts-legend-item-text {

    fill: #003366 !important; /* Navy for data points */

    color: #003366 !important;

    font-family: 'Inter', sans-serif !important;

}
 
/* 5. KPI & BIG NUMBERS: Prominent Navy with Bold Weight */

.big-number, 

.bigNumber, 

.dashboard-markdown h1,

.dashboard-component-chart-holder [class*="big-number"],

.dashboard-component-chart-holder [class*="BigNumber"] {

    color: #003366 !important;

    fill: #003366 !important;

    font-weight: 800 !important;

    font-size: 44px !important;

    text-shadow: none !important; /* Removed glow for light theme cleanliness */

}
 
/* 6. TABLES: Clean Navy on Light Glass */

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
 
.ant-table-thead > tr > th {

    font-weight: 700 !important;

    background: rgba(0, 51, 102, 0.03) !important;

    text-transform: uppercase;

}
 
/* 7. AXIS & GRID LINES: Subtle Gray */

.nvd3 .nv-axis path,

.nvd3 .nv-axis line,

.recharts-cartesian-grid-horizontal line,

.recharts-cartesian-grid-vertical line {

    stroke: rgba(0, 51, 102, 0.1) !important;

}
 
/* 8. LABELS & SUB-TEXT: EXL Orange Accents */

.chart-header .header-title {

    color: #334155 !important; /* Slate for titles */

    font-weight: 500 !important;

    text-transform: uppercase !important;

    font-size: 11px !important;

}
 
.dashboard-markdown p {

    color: #fb4e0b !important; /* EXL Orange for sub-labels */

    font-weight: 600 !important;

    text-transform: uppercase !important;

    letter-spacing: 0.8px;

}
 
/* 9. FILTER PANEL: Integrated White Glass */

.dashboard-filters-panel {

    background: rgba(255, 255, 255, 0.5) !important;

    backdrop-filter: blur(20px) !important;

    border-right: 1px solid rgba(251, 78, 11, 0.1) !important;

}
 
