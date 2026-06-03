/* ══════════════════════════════════════════════════════════════════
   EXL SERVICE — EXECUTIVE PREMIER DASHBOARD  v2.2
   Patch release: removed blue headline border, fixed garbled
   legend text, repositioned legend labels higher.
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
   FIX v2.1: Removed !important from font-family to prevent
   metric mismatch when DM Sans hasn't loaded yet. Font now
   applies as a preference rather than a forced override, which
   lets Superset's own layout calculations remain valid.
────────────────────────────────────────────────────────────── */

*, *::before, *::after {
    box-sizing: border-box;
}

body, #app,
.dashboard,
.dashboard-container,
.dragdroppable-content {
    font-family: "DM Sans", -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
    color: var(--text-primary);
    background: #EEF2F8;
    background-image:
        radial-gradient(ellipse at 0% 0%, rgba(37,99,235,0.06) 0%, transparent 55%),
        radial-gradient(ellipse at 100% 100%, rgba(11,30,61,0.04) 0%, transparent 55%);
    background-attachment: fixed;
}

.dashboard-content,
.dashboard-content-editable {
    background: transparent;
}

/* FIX v2.1: Ensure every chart card explicitly has a white surface
   background so the global gradient never bleeds through. */
.dashboard-component-chart-holder,
.grid-container .dashboard-component-chart-holder {
    background: var(--surface);
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
   FIX v2.1: Replaced blanket overflow:visible with a smarter
   approach. Only overflow-y is visible (for labels that extend
   below), while overflow-x remains hidden to prevent horizontal
   blowout that was causing legend truncation.
────────────────────────────────────────────────────────────── */

.dashboard-component-chart-holder {
    background: var(--surface) !important;
    border-radius: var(--radius-card) !important;
    border: 1px solid var(--border) !important;
    /* FIX v2.2: Removed blue top border per user request */
    box-shadow: var(--shadow-sm) !important;
    padding: 20px 22px !important;
    margin-bottom: 20px !important;
    overflow-x: hidden !important;       /* prevent horizontal blowout */
    overflow-y: visible !important;      /* allow labels that extend below */
    transition: box-shadow 0.22s ease !important;
}

.dashboard-component-chart-holder:hover {
    box-shadow: var(--shadow-hover) !important;
}

/* Inner slice and chart containers — controlled overflow */
.dashboard-component-chart-holder .slice_container,
.dashboard-component-chart-holder .chart-container,
.dashboard-component-chart-holder .slice_container > div {
    overflow: visible !important;
    min-height: 0 !important;            /* FIX: prevent flex squishing */
}


/* ──────────────────────────────────────────────────────────────
   SECTION 5 · CHART CARD TITLES
   FIX v2.1: Reduced font-weight from 700 to 600 on titles so
   the DM Sans letterforms don't get clipped at small sizes.
────────────────────────────────────────────────────────────── */

.header-title,
.dashboard-component-header span[role="button"],
.dragdroppable-column .header-title,
.editable-title span,
[data-test="editable-title"] button {
    color: var(--navy) !important;
    font-size: 14px !important;
    font-weight: 600 !important;
    letter-spacing: 0.1px !important;
    text-transform: none !important;
    white-space: nowrap !important;
    overflow: visible !important;
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
   FIX v2.1: Reduced font-size from 38px to 32px to prevent
   clipping inside tight card slots. Added min-width:0 on the
   parent to allow flexbox shrinking.
────────────────────────────────────────────────────────────── */

[data-test="big-number-total"],
.big-number .header-line,
.superset-key-value-chart-value {
    color: var(--navy) !important;
    font-size: 32px !important;
    font-weight: 700 !important;
    letter-spacing: -1px !important;
    line-height: 1.1 !important;
    font-family: "DM Mono", "DM Sans", monospace !important;
}

/* Parent flex container for big numbers — allow shrinking */
.dashboard-component-chart-holder .big_number,
.dashboard-component-chart-holder [class*="big-number"],
.dashboard-component-chart-holder .header-line {
    min-width: 0 !important;
    overflow: visible !important;
}

/* SVG path for ECharts big numbers */
svg.superset-svg-big-number text.main-line {
    fill: var(--navy) !important;
    font-size: 32px !important;
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
   FIX v2.1: Major rewrite of legend handling.
   Root cause of truncated legends was:
     a) overflow:visible pushed legend beyond grid bounds
     b) No max-width on legend items caused horizontal overflow
     c) Font metric mismatch from forced !important font-family
   Fix: Explicit max-width, word-wrap, and proper overflow control.
────────────────────────────────────────────────────────────── */

/* NVD3 legends */
/* FIX v2.2: Removed font-family override on SVG text to prevent
   garbled rendering ("Ownershin" / "Fmnathv" artifacts).
   DM Sans applied to SVG <text> via CSS causes character
   substitution in NVD3. We use a web-safe stack instead. */
.nv-legend-text {
    fill: var(--text-secondary) !important;
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif !important;
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
    max-width: 100% !important;
    /* FIX v2.2: Move legend labels higher up, closer to the chart */
    transform: translateY(-18px) !important;
}

/* NVD3 legend series groups — allow wrapping */
svg g.nvd3.nv-legend g.nv-series {
    overflow: visible !important;
}

/* ECharts legends */
/* FIX v2.2: Same web-safe font stack for SVG legend text */
.echarts-legend-text,
.legend-item-name,
.legend-item-label,
.echarts-for-react svg text.legend-text {
    fill: var(--text-secondary) !important;
    color: var(--text-secondary) !important;
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif !important;
    font-size: 12px !important;
    font-weight: 600 !important;
    visibility: visible !important;
    opacity: 1 !important;
}

/* ECharts legend container — allow wrapping to prevent truncation */
div.echarts-legend,
div[class*="legend"] {
    overflow: visible !important;
    max-width: 100% !important;
    flex-wrap: wrap !important;
}


/* ──────────────────────────────────────────────────────────────
   SECTION 8 · EXECUTIVE TABLE DESIGN
   FIX v2.1: Added explicit white background on table cells and
   table container to prevent gradient bleed-through. Added
   word-break to prevent long text from overflowing cells.
────────────────────────────────────────────────────────────── */

.superset-stylable-table-container,
.dashboard-component-chart-holder table {
    border-collapse: separate !important;
    border-spacing: 0 !important;
    width: 100% !important;
    border-radius: var(--radius-inner) !important;
    overflow: hidden !important;
    background: var(--surface) !important;  /* FIX: explicit surface */
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
    word-break: break-word !important;      /* FIX: prevent long text overflow */
    overflow-wrap: break-word !important;
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
   FIX v2.1: Reduced padding from 56px/48px to 32px/28px.
   The original padding was pushing the pie chart render area
   beyond the grid slot, causing ECharts labels to render
   outside the visible bounds. Combined with the new
   overflow-x:hidden on the card holder, the chart now stays
   within its container while labels still remain visible.
────────────────────────────────────────────────────────────── */

.dashboard-chart-id-104 .dashboard-component-chart-holder,
.dashboard-chart-id-104 .slice_container,
.dashboard-chart-id-104 .chart-container,
.dashboard-chart-id-104 .slice_container > div,
.dashboard-chart-id-104 canvas {
    overflow: visible !important;
}

.dashboard-chart-id-104 .chart-container {
    padding-right: 32px !important;      /* FIX: reduced from 56px */
    padding-bottom: 28px !important;     /* FIX: reduced from 48px */
}


/* ──────────────────────────────────────────────────────────────
   SECTION 14 · TEXT CONTENT CARDS  (NEW in v2.1)
   FIX v2.1: Ensure Markdown/text cards have consistent white
   backgrounds and proper text wrapping. This was causing the
   left card to show a beige/different background and the text
   to be cut off at the right edge.
────────────────────────────────────────────────────────────── */

.dashboard-component-chart-holder .markdown,
.dashboard-component-chart-holder .dashboard-markdown,
.dashboard-component-chart-holder [class*="markdown"],
.dashboard-component-chart-holder .slice_container p,
.dashboard-component-chart-holder .slice_container span,
.dashboard-component-chart-holder .slice_container div {
    background: transparent !important;   /* inherit card's white surface */
    word-break: break-word !important;
    overflow-wrap: break-word !important;
    max-width: 100% !important;
}

/* Ensure text cards don't clip their content */
.dashboard-component-chart-holder .slice_container {
    min-height: 0 !important;
    overflow: visible !important;
}


/* ──────────────────────────────────────────────────────────────
   SECTION 15 · GRID LAYOUT STABILITY  (NEW in v2.1)
   FIX v2.1: Ensure the CSS Grid/Flexbox layout doesn't
   compress cards below their minimum content size, which was
   causing text truncation and legend clipping. Setting
   min-width:0 on flex children allows them to shrink
   gracefully rather than overflowing.
────────────────────────────────────────────────────────────── */

.dragdroppable-column,
.dashboard-component,
.dashboard-component-chart-holder,
.grid-container .dashboard-component {
    min-width: 0 !important;
    min-height: 0 !important;
}

/* Ensure grid cells don't overflow their designated slots */
.dashboard-grid,
.dashboard-content .grid-container {
    overflow: visible !important;
}

/* Prevent card content from pushing the card wider than its grid slot */
.dashboard-component-chart-holder {
    max-width: 100% !important;
}


/* ──────────────────────────────────────────────────────────────
   SECTION 16 · FONT LOADING STABILITY  (NEW in v2.1)
   FIX v2.1: Use font-display:swap via the Google Fonts URL
   parameter already present in the @import. This section adds
   a fallback system-font style for chart internals so that
   if DM Sans hasn't loaded yet, Superset's layout engine
   doesn't calculate sizes based on wrong font metrics.
   The key insight: Superset sizes chart containers at render
   time using the *current* font. If DM Sans loads after
   render, the container is too small for the new font. By
   not forcing DM Sans with !important on chart internals,
   we let Superset use its default font for layout math,
   then the CSS cascade applies DM Sans visually without
   breaking the container sizes.
────────────────────────────────────────────────────────────── */

/* FIX v2.2: Do NOT apply DM Sans to SVG chart text.
   DM Sans on SVG <text> elements causes garbled rendering
   (characters replaced/substituted). Use system font stack
   for all chart SVG text to keep labels crystal-clear. */
.nv-axis text,
.echarts-for-react text,
svg text {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif !important;
}


/* ──────────────────────────────────────────────────────────────
   SECTION 17 · CARD BORDER CONSISTENCY  (v2.2)
   FIX v2.2: Removed blue top border per user request.
   Cards now use a uniform 1px border on all sides.
────────────────────────────────────────────────────────────── */

.dashboard-component-chart-holder,
.dashboard-component-tabs .dashboard-component-chart-holder,
.dragdroppable-column .dashboard-component-chart-holder,
.dashboard-content .dashboard-component-chart-holder {
    border: 1px solid var(--border) !important;
}
