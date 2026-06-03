/* ══════════════════════════════════════════════════════════════════
   EXL SERVICE — EXECUTIVE PREMIER DASHBOARD  v2.0
   Complete architecture rewrite. Zero rule conflicts.
   Design: Prussian-blue authority, clean white surfaces,
           amber data accents, DM Sans typography.
══════════════════════════════════════════════════════════════════ */

@import url('https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600;700;800&family=DM+Mono:wght@400;500&display=swap');


/* ──────────────────────────────────────────────────────────────
   SECTION 1 · DESIGN TOKENS
   All visual constants live here. Edit these to retheme.
────────────────────────────────────────────────────────────── */

:root {
    --navy:          #0B1E3D;
    --navy-mid:      #17326B;
    --blue:          #2563EB;
    --blue-light:    #3B82F6;
    --amber:         #F59E0B;
    --surface:       #FFFFFF;
    --surface-alt:   #F7F9FC;
    --border:        #DDE3EE;
    --border-strong: #C4CFDE;
    --text-primary:  #0D1B2A;
    --text-secondary:#3D5068;
    --text-muted:    #7C8FA6;
    --shadow-sm:     0 1px 3px rgba(11,30,61,0.07), 0 4px 12px rgba(11,30,61,0.05);
    --shadow-md:     0 2px 8px rgba(11,30,61,0.09), 0 12px 32px rgba(11,30,61,0.07);
    --shadow-hover:  0 4px 16px rgba(11,30,61,0.12), 0 20px 48px rgba(11,30,61,0.09);
    --radius-card:   14px;
    --radius-inner:  8px;
}


/* ──────────────────────────────────────────────────────────────
   SECTION 2 · GLOBAL BASE
────────────────────────────────────────────────────────────── */

*, *::before, *::after {
    box-sizing: border-box;
}

body, #app,
.dashboard,
.dashboard-container,
.dragdroppable-content {
    font-family: "DM Sans", -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif !important;
    color: var(--text-primary) !important;
    background: #EEF2F8 !important;
    background-image:
        radial-gradient(ellipse at 0% 0%, rgba(37,99,235,0.06) 0%, transparent 55%),
        radial-gradient(ellipse at 100% 100%, rgba(11,30,61,0.04) 0%, transparent 55%) !important;
    background-attachment: fixed !important;
}

.dashboard-content,
.dashboard-content-editable {
    background: transparent !important;
}


/* ──────────────────────────────────────────────────────────────
   SECTION 3 · DASHBOARD HEADER BAR
────────────────────────────────────────────────────────────── */

.dashboard-header,
.header-with-actions {
    background: var(--navy) !important;
    border-bottom: 2px solid var(--blue) !important;
    padding: 14px 28px !important;
    box-shadow: 0 4px 24px rgba(11,30,61,0.3) !important;
}

/* Header title text */
.dashboard-title,
[data-test="editable-title"] button,
[data-test="editable-title"] span {
    color: #FFFFFF !important;
    font-size: 18px !important;
    font-weight: 700 !important;
    letter-spacing: -0.2px !important;
}

/* Header action icons */
.dashboard-header .action-button,
.header-with-actions .action-button,
.dashboard-header button,
.header-with-actions button {
    color: rgba(255,255,255,0.7) !important;
    opacity: 1 !important;
    visibility: visible !important;
}

.dashboard-header button:hover,
.header-with-actions button:hover {
    color: #FFFFFF !important;
    background: rgba(255,255,255,0.12) !important;
    border-radius: 6px !important;
}


/* ──────────────────────────────────────────────────────────────
   SECTION 4 · CHART CARDS  (the main containers)
────────────────────────────────────────────────────────────── */

.dashboard-component-chart-holder {
    background: var(--surface) !important;
    border-radius: var(--radius-card) !important;
    border: 1px solid var(--border) !important;
    border-top: 3px solid var(--blue) !important;
    box-shadow: var(--shadow-sm) !important;
    padding: 20px 22px !important;
    margin-bottom: 20px !important;
    overflow: visible !important;        /* prevents label clipping in ALL charts */
    transition: box-shadow 0.22s ease, border-color 0.22s ease !important;
}

.dashboard-component-chart-holder:hover {
    box-shadow: var(--shadow-hover) !important;
    border-top-color: var(--amber) !important;
}

/* Inner slice and chart containers must also allow overflow */
.dashboard-component-chart-holder .slice_container,
.dashboard-component-chart-holder .chart-container,
.dashboard-component-chart-holder .slice_container > div {
    overflow: visible !important;
}


/* ──────────────────────────────────────────────────────────────
   SECTION 5 · CHART CARD TITLES
────────────────────────────────────────────────────────────── */

.header-title,
.dashboard-component-header span[role="button"],
.dragdroppable-column .header-title,
.editable-title span,
[data-test="editable-title"] button {
    color: var(--navy) !important;
    font-size: 14px !important;
    font-weight: 700 !important;
    letter-spacing: 0.1px !important;
    text-transform: none !important;
}

/* Subtitle / description line below chart title */
.dashboard-component-chart-holder .header-line + div {
    color: var(--text-muted) !important;
    font-size: 12px !important;
    font-weight: 500 !important;
    letter-spacing: 0.1px !important;
}


/* ──────────────────────────────────────────────────────────────
   SECTION 6 · KPI / BIG-NUMBER VALUES
────────────────────────────────────────────────────────────── */

[data-test="big-number-total"],
.big-number .header-line,
.superset-key-value-chart-value {
    color: var(--navy) !important;
    font-size: 38px !important;
    font-weight: 700 !important;
    letter-spacing: -1.5px !important;
    line-height: 1.05 !important;
    font-family: "DM Mono", "DM Sans", monospace !important;
}

/* SVG path for ECharts big numbers */
svg.superset-svg-big-number text.main-line {
    fill: var(--navy) !important;
    font-size: 38px !important;
    font-weight: 700 !important;
}

/* Comparison / trend text below the big number */
.big-number-chart svg text:not(.main-line) {
    fill: var(--text-muted) !important;
    font-size: 13px !important;
    font-weight: 500 !important;
}


/* ──────────────────────────────────────────────────────────────
   SECTION 7 · CHART LEGEND TEXT
   Explicit visibility on every selector Superset uses.
────────────────────────────────────────────────────────────── */

/* NVD3 legends */
.nv-legend-text {
    fill: var(--text-secondary) !important;
    font-size: 12px !important;
    font-weight: 600 !important;
    visibility: visible !important;
    opacity: 1 !important;
}

.nv-legendWrap,
svg g.nvd3.nv-legend,
.dashboard-component-chart-holder .nv-legendWrap,
.dashboard-component-chart-holder svg g.nvd3.nv-legend {
    visibility: visible !important;
    opacity: 1 !important;
    overflow: visible !important;
}

/* ECharts legends */
.echarts-legend-text,
.legend-item-name,
.legend-item-label,
.echarts-for-react svg text.legend-text {
    fill: var(--text-secondary) !important;
    color: var(--text-secondary) !important;
    font-size: 12px !important;
    font-weight: 600 !important;
    visibility: visible !important;
    opacity: 1 !important;
}


/* ──────────────────────────────────────────────────────────────
   SECTION 8 · EXECUTIVE TABLE DESIGN
────────────────────────────────────────────────────────────── */

.superset-stylable-table-container,
.dashboard-component-chart-holder table {
    border-collapse: separate !important;
    border-spacing: 0 !important;
    width: 100% !important;
    border-radius: var(--radius-inner) !important;
    overflow: hidden !important;
}

/* Table header row */
.dashboard-component-chart-holder thead tr th,
.ant-table-thead > tr > th {
    background: var(--navy) !important;
    color: #FFFFFF !important;
    font-weight: 700 !important;
    font-size: 12px !important;
    text-transform: uppercase !important;
    letter-spacing: 0.6px !important;
    padding: 14px 16px !important;
    border: none !important;
    white-space: nowrap !important;
}

/* Table body cells */
.dashboard-component-chart-holder tbody tr td,
.ant-table-tbody > tr > td {
    color: var(--text-primary) !important;
    font-weight: 500 !important;
    font-size: 13px !important;
    padding: 11px 16px !important;
    border-bottom: 1px solid var(--border) !important;
    background: var(--surface) !important;
}

/* Zebra striping */
.dashboard-component-chart-holder tbody tr:nth-child(even) td,
.ant-table-tbody > tr:nth-child(even) > td {
    background: var(--surface-alt) !important;
}

/* Row hover */
.dashboard-component-chart-holder tbody tr:hover td,
.ant-table-tbody > tr:hover > td {
    background: #EBF3FF !important;
}


/* ──────────────────────────────────────────────────────────────
   SECTION 9 · TABS (top-level & nested)
────────────────────────────────────────────────────────────── */

.ant-tabs-nav,
.dashboard-component-tabs .ant-tabs-nav {
    margin-bottom: 24px !important;
    border-bottom: 2px solid var(--border) !important;
    background: transparent !important;
    padding-top: 0 !important;
}

.ant-tabs-tab,
.dashboard-component-tabs .ant-tabs-tab,
.dashboard-content .ant-tabs-nav .ant-tabs-tab {
    color: var(--text-muted) !important;
    font-size: 14px !important;
    font-weight: 500 !important;
    padding: 10px 18px !important;
    transition: color 0.18s !important;
}

.ant-tabs-tab:hover {
    color: var(--blue) !important;
}

/* Active tab */
.ant-tabs-tab-active .ant-tabs-tab-btn,
.dashboard-component-tabs .ant-tabs-tab-active .ant-tabs-tab-btn,
.dashboard-content .ant-tabs-nav .ant-tabs-tab-active .ant-tabs-tab-btn {
    color: var(--navy) !important;
    font-weight: 800 !important;
}

/* Active tab indicator bar */
.ant-tabs-ink-bar,
.dashboard-component-tabs .ant-tabs-ink-bar {
    background: var(--blue) !important;
    height: 3px !important;
    border-radius: 3px 3px 0 0 !important;
}


/* ──────────────────────────────────────────────────────────────
   SECTION 10 · TOOLBAR & CHART ACTION BUTTONS
────────────────────────────────────────────────────────────── */

.dashboard-component-chart-holder .action-button,
.dashboard-component-chart-holder .header .dropdown-toggle {
    color: var(--text-muted) !important;
    opacity: 1 !important;
    visibility: visible !important;
}

.dashboard-component-chart-holder .action-button:hover {
    color: var(--blue) !important;
}


/* ──────────────────────────────────────────────────────────────
   SECTION 11 · ECHARTS TOOLTIP OVERRIDE
────────────────────────────────────────────────────────────── */

/* Prevent global color overrides from bleeding into tooltip */
.echarts-for-react .echarts-tooltip,
.echarts-for-react .echarts-toolbar {
    color: initial !important;
    fill: initial !important;
}


/* ──────────────────────────────────────────────────────────────
   SECTION 12 · SCROLLBARS
────────────────────────────────────────────────────────────── */

::-webkit-scrollbar              { width: 5px; height: 5px; }
::-webkit-scrollbar-track        { background: #EEF2F8; border-radius: 10px; }
::-webkit-scrollbar-thumb        { background: rgba(11,30,61,0.22); border-radius: 10px; }
::-webkit-scrollbar-thumb:hover  { background: rgba(11,30,61,0.42); }


/* ──────────────────────────────────────────────────────────────
   SECTION 13 · RURAL BREAKDOWN PIE CHART  (#104)
   ─────────────────────────────────────────────────────────────
   ROOT CAUSE: ECharts renders pie labels outside the canvas
   bounding box, causing them to be clipped by parent overflow.

   FIX STRATEGY (single unified approach, no conflicts):
   1. Set overflow:visible on every wrapper layer.
   2. Add breathing room via padding only on .chart-container,
      which expands the render area without touching the grid slot.
   No transform. No duplicate position rules.
────────────────────────────────────────────────────────────── */

.dashboard-chart-id-104 .dashboard-component-chart-holder,
.dashboard-chart-id-104 .slice_container,
.dashboard-chart-id-104 .chart-container,
.dashboard-chart-id-104 .slice_container > div,
.dashboard-chart-id-104 canvas {
    overflow: visible !important;
}

.dashboard-chart-id-104 .chart-container {
    padding-right: 56px !important;
    padding-bottom: 48px !important;
}


/* ──────────────────────────────────────────────────────────────
   SECTION 14 · ECHARTS LEGEND OVERFLOW & SELECTOR FIX
   ─────────────────────────────────────────────────────────────
   PROBLEM (visible in Behavior Scorecard):
   ECharts renders legend items + "All / Inv" selector buttons
   on a single line. When chart width is narrow the line
   overflows, items get clipped and selectors collide with
   legend text.

   FIX STRATEGY:
   1. Give every chart-holder extra bottom clearance so
      ECharts has room to flow the legend onto a second line.
   2. Style the ECharts legend selector buttons
      (the "All" and "Inv" pill buttons) so they are clearly
      separated from the legend items and look intentional
      rather than like overflow artefacts.
   3. Ensure the echarts canvas wrapper itself never clips
      the legend row.
────────────────────────────────────────────────────────────── */
