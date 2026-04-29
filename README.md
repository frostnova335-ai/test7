/******************************************************************

* EXL SERVICE EXECUTIVE PREMIERE - FINAL LEGEND & TYPOGRAPHY FIX

******************************************************************/
 
/* 1. CHART VALUES: DEEP BLUE (STRICT TARGETING) */

[data-test="big-number-total"],

.big-number,

.header-line,

.superset-key-value-chart-value,

svg.superset-svg-big-number text.main-line {

    fill: #032c62 !important;

    color: #032c62 !important;   

    font-weight: 700 !important;  

    font-size: 38px !important;   

    font-family: "Inter", sans-serif !important;

}
 
/* 2. LEGEND RESCUE: FORCE VISIBILITY AT BOTTOM */

/* This prevents the theme from hiding or whitening the legend text */

.dashboard-component-chart-holder svg g.nvd3.nv-legend,

.dashboard-component-chart-holder .echarts-chart div,

.dashboard-component-chart-holder .nv-legendWrap,

.nv-legend-text,

.legend-item-name {

    visibility: visible !important;

    opacity: 1 !important;

    display: block !important;

}
 
/* Ensure legend text is readable against the white card */

.nv-legend-text, .echarts-legend-text, .legend-text {

    fill: #334155 !important; /* Dark Slate Gray */

    color: #334155 !important;

    font-size: 12px !important;

    font-weight: 600 !important;

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
 
/* Subtitles */

.dashboard-component-chart-holder .header-line + div, 

.big-number-chart svg text:not(.main-line) {

    font-family: "Inter", sans-serif !important;

    font-weight: 500 !important;

    color: #64748b !important; 

    font-size: 13px !important;

    letter-spacing: 0.2px !important;

}
 
/* 4. FULL PAGE GRADIENT (WHITE TOP -> SOFT BLUE BOTTOM) */

body, #app, .dashboard, .dashboard-content, .dashboard-header, .header-with-actions, header {

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
 
/* 6. CHART CARDS: GLOW BORDERS (NO CLIPPING) */

.dashboard-component-chart-holder {

    background: linear-gradient(135deg, #ffffff 0%, rgba(255,255,255,0.9) 100%) !important;

    backdrop-filter: blur(20px) !important;

    border-radius: 20px !important;

    border: 2px solid transparent !important;

    background-clip: padding-box !important;

    /* Dual Border Effect using box-shadow only */

    box-shadow: 

        0 0 0 2px #ffffff, 

        0 0 0 4px rgba(135, 206, 250, 0.4), 

        0 10px 30px rgba(3, 44, 98, 0.08) !important;

    padding: 24px !important;

    margin-bottom: 24px !important;

    /* CRITICAL: Ensure legends aren't cut off */

    overflow: visible !important; 

}
 
/* 7. TABS & SCROLLBARS */

.ant-tabs-nav { margin-bottom: 30px !important; }

.ant-tabs-tab-active .ant-tabs-tab-btn {

    color: #032c62 !important;

    font-weight: 800 !important;

}
 
::-webkit-scrollbar { width: 5px; height: 5px; }

::-webkit-scrollbar-thumb {

    background: rgba(3, 44, 98, 0.3);

    border-radius: 10px;

}
 
