/**********************
 * EXL SERVICE EXECUTIVE PREMIERE — v3 STABLE
 *
 * Root causes fixed in this version:
 *
 * 1. LEGEND / LABEL CLIPPING ("In" truncation, pie labels cut off)
 *    overflow:hidden on the card was clipping NVD3/ECharts legends
 *    that render outside the chart SVG bounds. Fix: remove overflow
 *    from the card entirely and instead clip only the background
 *    using a pseudo-element so the visual border stays tight while
 *    chart content can overflow safely.
 *
 * 2. "deque mutated during iteration" ERRORS
 *    CSS transitions on chart holder elements (even inherited ones)
 *    can trigger React/ECharts to re-measure mid-render. Fix: set
 *    transition:none on all chart containers.
 *
 * 3. NVD3 LEGEND WRAP OVERFLOW
 *    .nv-legendWrap is an SVG <g> — setting overflow on it does
 *    nothing. The real fix is ensuring the chart card has enough
 *    vertical space and that the SVG viewBox is not clipped by a
 *    parent with overflow:hidden.
 *
 * 4. ECHARTS CANVAS INVISIBLE
 *    backdrop-filter on a parent creates a new stacking context
 *    that can hide canvas elements in Chromium. Kept removed.
 *
 * 5. TABLE BORDER-RADIUS WITH border-collapse:separate
 *    border-collapse:separate is required for border-radius on
 *    tables to work — kept, but removed the conflicting
 *    border-collapse:collapse that was also present.
 **********************/


/* ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
   1. PAGE BACKGROUND
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ */

body,
#app,
.dashboard,
.dashboard-content,
.dashboard-header,
.header-with-actions,
header {
    background-color: #f1f5f9 !important;
    background-image:
        radial-gradient(at 100% 100%, rgba(3, 44, 98, 0.04) 0px, transparent 50%),
        linear-gradient(180deg, #ffffff 0%, #f8fafc 40%, #f1f5f9 100%) !important;
    background-attachment: fixed !important;
}


/* ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
   2. CHART CARDS
   Strategy: do NOT clip the card element itself. Instead use a
   ::before pseudo-element to paint the white background + border
   + shadow, while the card element stays overflow:visible so that
   NVD3 legend wraps and ECharts labels are never cut off.
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ */

.dashboard-component-chart-holder {
    position: relative !important;
    /* No overflow property here — let chart content breathe */
    background: transparent !important;
    border-radius: 20px !important;
    border: none !important;
    box-shadow: none !important;
    padding: 24px !important;
    margin-bottom: 20px !important;
    /* Kill all transitions — prevents "deque mutated" render errors */
    transition: none !important;
}

/* White card background painted via pseudo so it doesn't clip children */
.dashboard-component-chart-holder::before {
    content: "" !important;
    position: absolute !important;
    inset: 0 !important;
    border-radius: 20px !important;
    background: #ffffff !important;
    border: 1px solid rgba(135, 206, 250, 0.4) !important;
    box-shadow:
        0 4px 20px rgba(3, 44, 98, 0.07),
        0 1px 4px rgba(3, 44, 98, 0.04) !important;
    pointer-events: none !important;
    z-index: 0 !important;
}

/* Chart content sits above the pseudo background */
.dashboard-component-chart-holder > * {
    position: relative !important;
    z-index: 1 !important;
}

/* Kill transitions on everything inside charts too */
.dashboard-component-chart-holder *,
.dashboard-component-chart-holder *::before,
.dashboard-component-chart-holder *::after {
    transition: none !important;
    animation-duration: 0.001ms !important; /* keeps JS animation callbacks firing but imperceptibly fast */
}

/* ── Chart inner wrappers: must be visible, not clipped ── */
.dashboard-component-chart-holder .chart-container,
.dashboard-component-chart-holder .nv-chart,
.dashboard-component-chart-holder .echarts-for-react,
.dashboard-component-chart-holder .slice_container {
    overflow: visible !important;
}

/* ── The SVG elements themselves must not be clipped ── */
.dashboard-component-chart-holder svg {
    overflow: visible !important;
}


/* ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
   3. BIG NUMBER / KPI
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ */

[data-test="big-number-total"],
.big-number,
.header-line,
.superset-key-value-chart-value {
    color: #032c62 !important;
    font-weight: 400 !important;
    font-size: 33px !important;
    font-family: "Inter", sans-serif !important;
}

svg.superset-svg-big-number text.main-line {
    fill: #032c62 !important;
    font-weight: 400 !important;
    font-size: 33px !important;
}


/* ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
   4. CHART TITLES & SUBTITLES
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ */

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

.big-number-chart svg text:not(.main-line) {
    font-family: "Inter", sans-serif !important;
    font-weight: 500 !important;
    fill: #64748b !important;
    font-size: 13px !important;
}


/* ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
   5. LEGENDS — NVD3 + ECHARTS
   Key insight: NVD3 renders legend as SVG <g> elements. Only
   fill/visibility/opacity work on SVG elements. display:block
   and color: break SVG layout entirely.
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ */

/* NVD3 legend container */
.dashboard-component-chart-holder svg .nv-legend,
.dashboard-component-chart-holder svg .nvd3.nv-legend,
.dashboard-component-chart-holder svg .nv-legendWrap {
    visibility: visible !important;
    opacity: 1 !important;
    /* Do NOT set display or overflow on SVG <g> elements */
}

/* NVD3 legend text labels */
.dashboard-component-chart-holder svg .nv-legend-text {
    fill: #334155 !important;
    font-size: 12px !important;
    font-weight: 600 !important;
}

/* NVD3 legend series symbols */
.dashboard-component-chart-holder svg .nv-legend .nv-series circle,
.dashboard-component-chart-holder svg .nv-legend .nv-series rect,
.dashboard-component-chart-holder svg .nv-legend .nv-series line {
    opacity: 1 !important;
    visibility: visible !important;
}

/* ECharts: legend items rendered as HTML divs */
.dashboard-component-chart-holder .echarts-for-react div[class*="legend"],
.dashboard-component-chart-holder .echarts-for-react .legend-item-name {
    color: #334155 !important;
    font-size: 12px !important;
    opacity: 1 !important;
    visibility: visible !important;
}


/* ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
   6. AXIS LABELS & TICK TEXT
   Scoped tightly — only target axis text, not series labels
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ */

.dashboard-component-chart-holder svg .nv-axis text,
.dashboard-component-chart-holder svg .axis text,
.dashboard-component-chart-holder svg .tick text {
    fill: #64748b !important;
    font-size: 11px !important;
}


/* ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
   7. TABLE
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ */

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
    background: #032c62 !important;
    color: #ffffff !important;
    font-weight: 700 !important;
    font-size: 14px !important;
    padding: 14px 15px !important;
    border: none !important;
}

/* First/last header cells: rounded corners */
.dashboard-component-chart-holder thead tr th:first-child,
.ant-table-thead > tr > th:first-child {
    border-top-left-radius: 10px !important;
}
.dashboard-component-chart-holder thead tr th:last-child,
.ant-table-thead > tr > th:last-child {
    border-top-right-radius: 10px !important;
}

.dashboard-component-chart-holder tbody tr td,
.ant-table-tbody > tr > td {
    font-weight: 500 !important;
    color: #1e293b !important;
    padding: 12px 15px !important;
    font-size: 14px !important;
    border-bottom: 1px solid #e2e8f0 !important;
    background: #ffffff !important;
}

/* Zebra rows */
.dashboard-component-chart-holder tbody tr:nth-child(even) td,
.ant-table-tbody > tr:nth-child(even) > td {
    background: #f8fafc !important;
}

/* Remove bottom border on last row */
.dashboard-component-chart-holder tbody tr:last-child td {
    border-bottom: none !important;
}


/* ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
   8. TABS
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ */

.ant-tabs-nav {
    margin-bottom: 24px !important;
}

.ant-tabs-tab-active .ant-tabs-tab-btn {
    color: #032c62 !important;
    font-weight: 700 !important;
}

.ant-tabs-ink-bar {
    background: #032c62 !important;
}


/* ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
   9. SCROLLBARS
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ */

::-webkit-scrollbar {
    width: 5px;
    height: 5px;
}

::-webkit-scrollbar-thumb {
    background: rgba(3, 44, 98, 0.25);
    border-radius: 10px;
}

::-webkit-scrollbar-track {
    background: transparent;
}


/* ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
   10. ERROR STATE
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ */

.dashboard-component-chart-holder .chart-error-message,
.dashboard-component-chart-holder [class*="error-message"] {
    color: #64748b !important;
    font-size: 13px !important;
}
