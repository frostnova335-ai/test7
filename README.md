456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BigNumber/BigNumberPeriodOverPeriod/controlPanel.ts:19:13
456.0 TS2305: Module '"@superset-ui/core"' has no exported member 'GenericDataType'.
456.0     17 |  * under the License.
456.0     18 |  */
456.0   > 19 | import { t, GenericDataType } from '@superset-ui/core';
456.0        |             ^^^^^^^^^^^^^^^
456.0     20 | import {
456.0     21 |   ControlPanelConfig,
456.0     22 |   getStandardizedControls,
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BigNumber/BigNumberPeriodOverPeriod/index.ts:46:31
456.0 TS6142: Module './PopKPI' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/BigNumber/BigNumberPeriodOverPeriod/PopKPI.tsx', but '--jsx' is not set.
456.0     44 |       buildQuery,
456.0     45 |       controlPanel,
456.0   > 46 |       loadChart: () => import('./PopKPI'),
456.0        |                               ^^^^^^^^^^
456.0     47 |       metadata,
456.0     48 |       transformProps,
456.0     49 |     });
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BigNumber/BigNumberPeriodOverPeriod/PopKPI.tsx:172:20
456.0 TS2339: Property 'colors' does not exist on type 'Theme'.
456.0     170 |   const getArrowIndicatorColor = () => {
456.0     171 |     if (!comparisonColorEnabled || percentDifferenceNumber === 0) {
456.0   > 172 |       return theme.colors.grayscale.base;
456.0         |                    ^^^^^^
456.0     173 |     }
456.0     174 |
456.0     175 |     if (percentDifferenceNumber > 0) {
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BigNumber/BigNumberPeriodOverPeriod/PopKPI.tsx:193:34
456.0 TS2339: Property 'colors' does not exist on type 'Theme'.
456.0     191 |
456.0     192 |   const defaultBackgroundColor = theme.colorBgContainer;
456.0   > 193 |   const defaultTextColor = theme.colors.grayscale.base;
456.0         |                                  ^^^^^^
456.0     194 |   const { backgroundColor, textColor } = useMemo(() => {
456.0     195 |     let bgColor = defaultBackgroundColor;
456.0     196 |     let txtColor = defaultTextColor;
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BigNumber/BigNumberPeriodOverPeriod/PopKPI.tsx:206:17
456.0 TS2339: Property 'colors' does not exist on type 'Theme'.
456.0     204 |       // Set background and text colors based on the conditions
456.0     205 |       bgColor = useSuccess
456.0   > 206 |         ? theme.colors.success.light2
456.0         |                 ^^^^^^
456.0     207 |         : theme.colors.error.light2;
456.0     208 |       txtColor = useSuccess ? theme.colorSuccess : theme.colorError;
456.0     209 |     }
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BigNumber/BigNumberPeriodOverPeriod/PopKPI.tsx:207:17
456.0 TS2339: Property 'colors' does not exist on type 'Theme'.
456.0     205 |       bgColor = useSuccess
456.0     206 |         ? theme.colors.success.light2
456.0   > 207 |         : theme.colors.error.light2;
456.0         |                 ^^^^^^
456.0     208 |       txtColor = useSuccess ? theme.colorSuccess : theme.colorError;
456.0     209 |     }
456.0     210 |
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BigNumber/BigNumberPeriodOverPeriod/PopKPI.tsx:268:5
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     266 |
456.0     267 |   return (
456.0   > 268 |     <div css={wrapperDivStyles} ref={wrapperRef}>
456.0         |     ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0     269 |       <NumbersContainer
456.0     270 |         css={
456.0     271 |           isOverflowing &&
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BigNumber/BigNumberPeriodOverPeriod/PopKPI.tsx:268:10
456.0 TS2322: Type '{ children: Element; css: SerializedStyles; ref: MutableRefObject<HTMLDivElement>; }' is not assignable to type 'DetailedHTMLProps<HTMLAttributes<HTMLDivElement>, HTMLDivElement>'.
456.0   Property 'css' does not exist on type 'DetailedHTMLProps<HTMLAttributes<HTMLDivElement>, HTMLDivElement>'.
456.0     266 |
456.0     267 |   return (
456.0   > 268 |     <div css={wrapperDivStyles} ref={wrapperRef}>
456.0         |          ^^^
456.0     269 |       <NumbersContainer
456.0     270 |         css={
456.0     271 |           isOverflowing &&
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BigNumber/BigNumberPeriodOverPeriod/PopKPI.tsx:269:7
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     267 |   return (
456.0     268 |     <div css={wrapperDivStyles} ref={wrapperRef}>
456.0   > 269 |       <NumbersContainer
456.0         |       ^^^^^^^^^^^^^^^^^
456.0   > 270 |         css={
456.0         | ^^^^^^^^^^^^^
456.0   > 271 |           isOverflowing &&
456.0         | ^^^^^^^^^^^^^
456.0   > 272 |           css`
456.0         | ^^^^^^^^^^^^^
456.0   > 273 |             width: fit-content;
456.0         | ^^^^^^^^^^^^^
456.0   > 274 |             margin: auto;
456.0         | ^^^^^^^^^^^^^
456.0   > 275 |             align-items: flex-start;
456.0         | ^^^^^^^^^^^^^
456.0   > 276 |             overflow: auto;
456.0         | ^^^^^^^^^^^^^
456.0   > 277 |           `
456.0         | ^^^^^^^^^^^^^
456.0   > 278 |         }
456.0         | ^^^^^^^^^^^^^
456.0   > 279 |       >
456.0         | ^^^^^^^^
456.0     280 |         {showMetricName && metricName && (
456.0     281 |           <MetricNameText metricNameFontSize={metricNameFontSize}>
456.0     282 |             {metricName}
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BigNumber/BigNumberPeriodOverPeriod/PopKPI.tsx:270:9
456.0 TS2322: Type '{ children: Element[]; css: SerializedStyles; }' is not assignable to type 'IntrinsicAttributes & { theme?: Theme; as?: ElementType<any>; } & ClassAttributes<HTMLDivElement> & HTMLAttributes<...> & { ...; }'.
456.0   Property 'css' does not exist on type 'IntrinsicAttributes & { theme?: Theme; as?: ElementType<any>; } & ClassAttributes<HTMLDivElement> & HTMLAttributes<...> & { ...; }'.
456.0     268 |     <div css={wrapperDivStyles} ref={wrapperRef}>
456.0     269 |       <NumbersContainer
456.0   > 270 |         css={
456.0         |         ^^^
456.0     271 |           isOverflowing &&
456.0     272 |           css`
456.0     273 |             width: fit-content;
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BigNumber/BigNumberPeriodOverPeriod/PopKPI.tsx:281:11
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     279 |       >
456.0     280 |         {showMetricName && metricName && (
456.0   > 281 |           <MetricNameText metricNameFontSize={metricNameFontSize}>
456.0         |           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0     282 |             {metricName}
456.0     283 |           </MetricNameText>
456.0     284 |         )}
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BigNumber/BigNumberPeriodOverPeriod/PopKPI.tsx:286:9
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     284 |         )}
456.0     285 |
456.0   > 286 |         <div css={bigValueContainerStyles}>
456.0         |         ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0     287 |           {bigNumber}
456.0     288 |           {percentDifferenceNumber !== 0 && (
456.0     289 |             <span css={arrowIndicatorStyle}>
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BigNumber/BigNumberPeriodOverPeriod/PopKPI.tsx:286:14
456.0 TS2322: Type '{ children: (string | Element)[]; css: SerializedStyles; }' is not assignable to type 'DetailedHTMLProps<HTMLAttributes<HTMLDivElement>, HTMLDivElement>'.
456.0   Property 'css' does not exist on type 'DetailedHTMLProps<HTMLAttributes<HTMLDivElement>, HTMLDivElement>'.
456.0     284 |         )}
456.0     285 |
456.0   > 286 |         <div css={bigValueContainerStyles}>
456.0         |              ^^^
456.0     287 |           {bigNumber}
456.0     288 |           {percentDifferenceNumber !== 0 && (
456.0     289 |             <span css={arrowIndicatorStyle}>
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BigNumber/BigNumberPeriodOverPeriod/PopKPI.tsx:289:13
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     287 |           {bigNumber}
456.0     288 |           {percentDifferenceNumber !== 0 && (
456.0   > 289 |             <span css={arrowIndicatorStyle}>
456.0         |             ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0     290 |               {percentDifferenceNumber > 0 ? '↑' : '↓'}
456.0     291 |             </span>
456.0     292 |           )}
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BigNumber/BigNumberPeriodOverPeriod/PopKPI.tsx:289:19
456.0 TS2322: Type '{ children: string; css: SerializedStyles; }' is not assignable to type 'DetailedHTMLProps<HTMLAttributes<HTMLSpanElement>, HTMLSpanElement>'.
456.0   Property 'css' does not exist on type 'DetailedHTMLProps<HTMLAttributes<HTMLSpanElement>, HTMLSpanElement>'.
456.0     287 |           {bigNumber}
456.0     288 |           {percentDifferenceNumber !== 0 && (
456.0   > 289 |             <span css={arrowIndicatorStyle}>
456.0         |                   ^^^
456.0     290 |               {percentDifferenceNumber > 0 ? '↑' : '↓'}
456.0     291 |             </span>
456.0     292 |           )}
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BigNumber/BigNumberPeriodOverPeriod/PopKPI.tsx:295:11
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     293 |         </div>
456.0     294 |         {subtitle && (
456.0   > 295 |           <SubtitleText
456.0         |           ^^^^^^^^^^^^^
456.0   > 296 |             style={{
456.0         | ^^^^^^^^^^^^^^^^^^^^
456.0   > 297 |               fontSize: `${subtitleFontSize * height * 0.4}px`,
456.0         | ^^^^^^^^^^^^^^^^^^^^
456.0   > 298 |             }}
456.0         | ^^^^^^^^^^^^^^^^^^^^
456.0   > 299 |           >
456.0         | ^^^^^^^^^^^^
456.0     300 |             {subtitle}
456.0     301 |           </SubtitleText>
456.0     302 |         )}
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BigNumber/BigNumberPeriodOverPeriod/PopKPI.tsx:305:11
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     303 |
456.0     304 |         {visibleSymbols.length > 0 && (
456.0   > 305 |           <div
456.0         |           ^^^^
456.0   > 306 |             css={[
456.0         | ^^^^^^^^^^^^^^^^^^
456.0   > 307 |               css`
456.0         | ^^^^^^^^^^^^^^^^^^
456.0   > 308 |                 display: flex;
456.0         | ^^^^^^^^^^^^^^^^^^
456.0   > 309 |                 justify-content: space-around;
456.0         | ^^^^^^^^^^^^^^^^^^
456.0   > 310 |                 gap: ${flexGap}px;
456.0         | ^^^^^^^^^^^^^^^^^^
456.0   > 311 |                 min-width: 0;
456.0         | ^^^^^^^^^^^^^^^^^^
456.0   > 312 |                 flex-shrink: 1;
456.0         | ^^^^^^^^^^^^^^^^^^
456.0   > 313 |               `,
456.0         | ^^^^^^^^^^^^^^^^^^
456.0   > 314 |               isOverflowing
456.0         | ^^^^^^^^^^^^^^^^^^
456.0   > 315 |                 ? css`
456.0         | ^^^^^^^^^^^^^^^^^^
456.0   > 316 |                     flex-direction: column;
456.0         | ^^^^^^^^^^^^^^^^^^
456.0   > 317 |                     align-items: flex-start;
456.0         | ^^^^^^^^^^^^^^^^^^
456.0   > 318 |                     width: fit-content;
456.0         | ^^^^^^^^^^^^^^^^^^
456.0   > 319 |                   `
456.0         | ^^^^^^^^^^^^^^^^^^
456.0   > 320 |                 : css`
456.0         | ^^^^^^^^^^^^^^^^^^
456.0   > 321 |                     align-items: center;
456.0         | ^^^^^^^^^^^^^^^^^^
456.0   > 322 |                     width: 100%;
456.0         | ^^^^^^^^^^^^^^^^^^
456.0   > 323 |                   `,
456.0         | ^^^^^^^^^^^^^^^^^^
456.0   > 324 |             ]}
456.0         | ^^^^^^^^^^^^^^^^^^
456.0   > 325 |             ref={symbolContainerRef}
456.0         | ^^^^^^^^^^^^^^^^^^
456.0   > 326 |           >
456.0         | ^^^^^^^^^^^^
456.0     327 |             {visibleSymbols.map((symbol_with_value, index) => (
456.0     328 |               <ComparisonValue
456.0     329 |                 key={`comparison-symbol-${symbol_with_value.columnKey}`}
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BigNumber/BigNumberPeriodOverPeriod/PopKPI.tsx:306:13
456.0 TS2322: Type '{ children: Element[]; css: SerializedStyles[]; ref: MutableRefObject<HTMLDivElement>; }' is not assignable to type 'DetailedHTMLProps<HTMLAttributes<HTMLDivElement>, HTMLDivElement>'.
456.0   Property 'css' does not exist on type 'DetailedHTMLProps<HTMLAttributes<HTMLDivElement>, HTMLDivElement>'.
456.0     304 |         {visibleSymbols.length > 0 && (
456.0     305 |           <div
456.0   > 306 |             css={[
456.0         |             ^^^
456.0     307 |               css`
456.0     308 |                 display: flex;
456.0     309 |                 justify-content: space-around;
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BigNumber/BigNumberPeriodOverPeriod/PopKPI.tsx:328:15
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     326 |           >
456.0     327 |             {visibleSymbols.map((symbol_with_value, index) => (
456.0   > 328 |               <ComparisonValue
456.0         |               ^^^^^^^^^^^^^^^^
456.0   > 329 |                 key={`comparison-symbol-${symbol_with_value.columnKey}`}
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 330 |                 subheaderFontSize={subheaderFontSize}
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 331 |               >
456.0         | ^^^^^^^^^^^^^^^^
456.0     332 |                 <Tooltip
456.0     333 |                   id="tooltip"
456.0     334 |                   placement="top"
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BigNumber/BigNumberPeriodOverPeriod/PopKPI.tsx:332:17
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     330 |                 subheaderFontSize={subheaderFontSize}
456.0     331 |               >
456.0   > 332 |                 <Tooltip
456.0         |                 ^^^^^^^^
456.0   > 333 |                   id="tooltip"
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 334 |                   placement="top"
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 335 |                   title={symbol_with_value.tooltipText}
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 336 |                 >
456.0         | ^^^^^^^^^^^^^^^^^^
456.0     337 |                   {symbol_with_value.symbol && (
456.0     338 |                     <SymbolWrapper
456.0     339 |                       backgroundColor={
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BigNumber/BigNumberPeriodOverPeriod/PopKPI.tsx:338:21
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     336 |                 >
456.0     337 |                   {symbol_with_value.symbol && (
456.0   > 338 |                     <SymbolWrapper
456.0         |                     ^^^^^^^^^^^^^^
456.0   > 339 |                       backgroundColor={
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 340 |                         index > 0 ? backgroundColor : defaultBackgroundColor
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 341 |                       }
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 342 |                       textColor={index > 0 ? textColor : defaultTextColor}
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 343 |                     >
456.0         | ^^^^^^^^^^^^^^^^^^^^^^
456.0     344 |                       {symbol_with_value.symbol}
456.0     345 |                     </SymbolWrapper>
456.0     346 |                   )}
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BigNumber/BigNumberPeriodOverPeriod/transformProps.ts:19:8
456.0 TS1259: Module '"/app/superset-frontend/node_modules/dayjs/index"' can only be default-imported using the 'esModuleInterop' flag
456.0     17 |  * under the License.
456.0     18 |  */
456.0   > 19 | import dayjs from 'dayjs';
456.0        |        ^^^^^
456.0     20 | import utc from 'dayjs/plugin/utc';
456.0     21 | import { Metric } from '@superset-ui/chart-controls';
456.0     22 | import {
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BigNumber/BigNumberPeriodOverPeriod/transformProps.ts:20:8
456.0 TS1259: Module '"/app/superset-frontend/node_modules/dayjs/plugin/utc"' can only be default-imported using the 'esModuleInterop' flag
456.0     18 |  */
456.0     19 | import dayjs from 'dayjs';
456.0   > 20 | import utc from 'dayjs/plugin/utc';
456.0        |        ^^^
456.0     21 | import { Metric } from '@superset-ui/chart-controls';
456.0     22 | import {
456.0     23 |   ChartProps,
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BigNumber/BigNumberPeriodOverPeriod/transformProps.ts:177:42
456.0 TS2362: The left-hand side of an arithmetic operation must be of type 'any', 'number', 'bigint' or an enum type.
456.0     175 |   const formatPercentChange = getNumberFormatter(percentDifferenceFormat);
456.0     176 |
456.0   > 177 |   let valueDifference: number | string = bigNumber - prevNumber;
456.0         |                                          ^^^^^^^^^
456.0     178 |
456.0     179 |   let percentDifferenceNum;
456.0     180 |
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BigNumber/BigNumberPeriodOverPeriod/transformProps.ts:177:54
456.0 TS2363: The right-hand side of an arithmetic operation must be of type 'any', 'number', 'bigint' or an enum type.
456.0     175 |   const formatPercentChange = getNumberFormatter(percentDifferenceFormat);
456.0     176 |
456.0   > 177 |   let valueDifference: number | string = bigNumber - prevNumber;
456.0         |                                                      ^^^^^^^^^^
456.0     178 |
456.0     179 |   let percentDifferenceNum;
456.0     180 |
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BigNumber/BigNumberPeriodOverPeriod/transformProps.ts:186:29
456.0 TS2362: The left-hand side of an arithmetic operation must be of type 'any', 'number', 'bigint' or an enum type.
456.0     184 |     percentDifferenceNum = bigNumber ? 1 : -1;
456.0     185 |   } else {
456.0   > 186 |     percentDifferenceNum = (bigNumber - prevNumber) / Math.abs(prevNumber);
456.0         |                             ^^^^^^^^^
456.0     187 |   }
456.0     188 |
456.0     189 |   const compType =
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BigNumber/BigNumberPeriodOverPeriod/transformProps.ts:186:41
456.0 TS2363: The right-hand side of an arithmetic operation must be of type 'any', 'number', 'bigint' or an enum type.
456.0     184 |     percentDifferenceNum = bigNumber ? 1 : -1;
456.0     185 |   } else {
456.0   > 186 |     percentDifferenceNum = (bigNumber - prevNumber) / Math.abs(prevNumber);
456.0         |                                         ^^^^^^^^^^
456.0     187 |   }
456.0     188 |
456.0     189 |   const compType =
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BigNumber/BigNumberPeriodOverPeriod/transformProps.ts:186:64
456.0 TS2345: Argument of type 'string | number' is not assignable to parameter of type 'number'.
456.0   Type 'string' is not assignable to type 'number'.
456.0     184 |     percentDifferenceNum = bigNumber ? 1 : -1;
456.0     185 |   } else {
456.0   > 186 |     percentDifferenceNum = (bigNumber - prevNumber) / Math.abs(prevNumber);
456.0         |                                                                ^^^^^^^^^^
456.0     187 |   }
456.0     188 |
456.0     189 |   const compType =
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BigNumber/BigNumberPeriodOverPeriod/transformProps.ts:191:31
456.0 TS2345: Argument of type 'string | number' is not assignable to parameter of type 'number'.
456.0   Type 'string' is not assignable to type 'number'.
456.0     189 |   const compType =
456.0     190 |     compTitles[formData.timeComparison as keyof typeof compTitles];
456.0   > 191 |   bigNumber = numberFormatter(bigNumber);
456.0         |                               ^^^^^^^^^
456.0     192 |   prevNumber = numberFormatter(prevNumber);
456.0     193 |   valueDifference = numberFormatter(valueDifference);
456.0     194 |   const percentDifference: string = formatPercentChange(percentDifferenceNum);
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BigNumber/BigNumberPeriodOverPeriod/transformProps.ts:192:32
456.0 TS2345: Argument of type 'string | number' is not assignable to parameter of type 'number'.
456.0   Type 'string' is not assignable to type 'number'.
456.0     190 |     compTitles[formData.timeComparison as keyof typeof compTitles];
456.0     191 |   bigNumber = numberFormatter(bigNumber);
456.0   > 192 |   prevNumber = numberFormatter(prevNumber);
456.0         |                                ^^^^^^^^^^
456.0     193 |   valueDifference = numberFormatter(valueDifference);
456.0     194 |   const percentDifference: string = formatPercentChange(percentDifferenceNum);
456.0     195 |
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BigNumber/BigNumberTotal/controlPanel.ts:19:10
456.0 TS2305: Module '"@superset-ui/core"' has no exported member 'GenericDataType'.
456.0     17 |  * under the License.
456.0     18 |  */
456.0   > 19 | import { GenericDataType, SMART_DATE_ID, t } from '@superset-ui/core';
456.0        |          ^^^^^^^^^^^^^^^
456.0     20 | import {
456.0     21 |   ControlPanelConfig,
456.0     22 |   D3_FORMAT_DOCS,
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BigNumber/BigNumberTotal/index.ts:58:31
456.0 TS6142: Module '../BigNumberViz' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/BigNumber/BigNumberViz.tsx', but '--jsx' is not set.
456.0     56 |   constructor() {
456.0     57 |     super({
456.0   > 58 |       loadChart: () => import('../BigNumberViz'),
456.0        |                               ^^^^^^^^^^^^^^^^^
456.0     59 |       metadata,
456.0     60 |       buildQuery,
456.0     61 |       transformProps,
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BigNumber/BigNumberTotal/transformProps.test.ts:20:10
456.0 TS2305: Module '"@superset-ui/core"' has no exported member 'GenericDataType'.
456.0     18 |  */
456.0     19 |
456.0   > 20 | import { GenericDataType } from '@superset-ui/core';
456.0        |          ^^^^^^^^^^^^^^^
456.0     21 | import { getColorFormatters } from '@superset-ui/chart-controls';
456.0     22 | import { BigNumberTotalChartProps } from '../types';
456.0     23 | import transformProps from './transformProps';
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BigNumber/BigNumberTotal/transformProps.ts:25:3
456.0 TS2305: Module '"@superset-ui/core"' has no exported member 'GenericDataType'.
456.0     23 | } from '@superset-ui/chart-controls';
456.0     24 | import {
456.0   > 25 |   GenericDataType,
456.0        |   ^^^^^^^^^^^^^^^
456.0     26 |   getMetricLabel,
456.0     27 |   extractTimegrain,
456.0     28 |   QueryFormData,
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BigNumber/BigNumberViz.tsx:31:20
456.0 TS6142: Module '../components/Echart' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/components/Echart.tsx', but '--jsx' is not set.
456.0     29 |   themeObject,
456.0     30 | } from '@superset-ui/core';
456.0   > 31 | import Echart from '../components/Echart';
456.0        |                    ^^^^^^^^^^^^^^^^^^^^^^
456.0     32 | import { BigNumberVizProps } from './types';
456.0     33 | import { EventHandlers } from '../types';
456.0     34 |
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BigNumber/BigNumberViz.tsx:125:7
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     123 |     if (!formatTime || !bigNumberFallback || showTimestamp) return null;
456.0     124 |     return (
456.0   > 125 |       <span
456.0         |       ^^^^^
456.0   > 126 |         className="alert alert-warning"
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 127 |         role="alert"
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 128 |         title={t(
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 129 |           `Last available value seen on %s`,
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 130 |           formatTime(bigNumberFallback[0]),
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 131 |         )}
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 132 |       >
456.0         | ^^^^^^^^
456.0     133 |         {t('Not up to date')}
456.0     134 |       </span>
456.0     135 |     );
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BigNumber/BigNumberViz.tsx:156:7
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     154 |
456.0     155 |     return (
456.0   > 156 |       <div
456.0         |       ^^^^
456.0   > 157 |         ref={this.metricNameRef}
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 158 |         className="metric-name"
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 159 |         style={{
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 160 |           fontSize,
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 161 |           height: 'auto',
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 162 |         }}
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 163 |       >
456.0         | ^^^^^^^^
456.0     164 |         {text}
456.0     165 |       </div>
456.0     166 |     );
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BigNumber/BigNumberViz.tsx:194:7
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     192 |
456.0     193 |     return (
456.0   > 194 |       <div
456.0         |       ^^^^
456.0   > 195 |         ref={this.kickerRef}
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 196 |         className="kicker"
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 197 |         style={{
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 198 |           fontSize,
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 199 |           height: 'auto',
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 200 |         }}
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 201 |       >
456.0         | ^^^^^^^^
456.0     202 |         {text}
456.0     203 |       </div>
456.0     204 |     );
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BigNumber/BigNumberViz.tsx:251:7
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     249 |
456.0     250 |     return (
456.0   > 251 |       <div
456.0         |       ^^^^
456.0   > 252 |         ref={this.headerRef}
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 253 |         className="header-line"
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 254 |         style={{
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 255 |           display: 'flex',
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 256 |           alignItems: 'center',
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 257 |           fontSize,
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 258 |           height: 'auto',
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 259 |           color: numberColor,
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 260 |         }}
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 261 |         onContextMenu={onContextMenu}
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 262 |       >
456.0         | ^^^^^^^^
456.0     263 |         {text}
456.0     264 |       </div>
456.0     265 |     );
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BigNumber/BigNumberViz.tsx:290:9
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     288 |
456.0     289 |       return (
456.0   > 290 |         <div
456.0         |         ^^^^
456.0   > 291 |           ref={this.subheaderRef}
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 292 |           className="subheader-line"
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 293 |           style={{
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 294 |             fontSize,
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 295 |             height: maxHeight,
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 296 |           }}
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 297 |         >
456.0         | ^^^^^^^^^^
456.0     298 |           {text}
456.0     299 |         </div>
456.0     300 |       );
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BigNumber/BigNumberViz.tsx:335:9
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     333 |
456.0     334 |       return (
456.0   > 335 |         <>
456.0         |         ^^
456.0     336 |           <div
456.0     337 |             ref={this.subtitleRef}
456.0     338 |             className="subtitle-line subheader-line"
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BigNumber/BigNumberViz.tsx:336:11
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     334 |       return (
456.0     335 |         <>
456.0   > 336 |           <div
456.0         |           ^^^^
456.0   > 337 |             ref={this.subtitleRef}
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 338 |             className="subtitle-line subheader-line"
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 339 |             style={{
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 340 |               fontSize: `${fontSize}px`,
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 341 |               height: maxHeight,
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 342 |             }}
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 343 |           >
456.0         | ^^^^^^^^^^^^
456.0     344 |             {text}
456.0     345 |           </div>
456.0     346 |         </>
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BigNumber/BigNumberViz.tsx:387:9
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     385 |     return (
456.0     386 |       echartOptions && (
456.0   > 387 |         <Echart
456.0         |         ^^^^^^^
456.0   > 388 |           refs={refs}
456.0         | ^^^^^^^^^^^^^^^^^^^^^
456.0   > 389 |           width={Math.floor(width)}
456.0         | ^^^^^^^^^^^^^^^^^^^^^
456.0   > 390 |           height={maxHeight}
456.0         | ^^^^^^^^^^^^^^^^^^^^^
456.0   > 391 |           echartOptions={echartOptions}
456.0         | ^^^^^^^^^^^^^^^^^^^^^
456.0   > 392 |           eventHandlers={eventHandlers}
456.0         | ^^^^^^^^^^^^^^^^^^^^^
456.0   > 393 |         />
456.0         | ^^^^^^^^^^^
456.0     394 |       )
456.0     395 |     );
456.0     396 |   }
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BigNumber/BigNumberViz.tsx:445:9
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     443 |
456.0     444 |       return (
456.0   > 445 |         <div className={className}>
456.0         |         ^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0     446 |           <div
456.0     447 |             className="text-container"
456.0     448 |             style={{
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BigNumber/BigNumberViz.tsx:446:11
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     444 |       return (
456.0     445 |         <div className={className}>
456.0   > 446 |           <div
456.0         |           ^^^^
456.0   > 447 |             className="text-container"
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 448 |             style={{
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 449 |               height: allTextHeight,
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 450 |               ...(shouldApplyOverflow
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 451 |                 ? {
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 452 |                     display: 'block',
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 453 |                     boxSizing: 'border-box',
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 454 |                     overflowX: 'hidden',
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 455 |                     overflowY: 'auto',
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 456 |                     width: '100%',
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 457 |                   }
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 458 |                 : {}),
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 459 |             }}
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 460 |           >
456.0         | ^^^^^^^^^^^^
456.0     461 |             {this.renderFallbackWarning()}
456.0     462 |             {this.renderMetricName(
456.0     463 |               Math.ceil(
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BigNumber/BigNumberViz.tsx:490:7
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     488 |     const shouldApplyOverflow = this.shouldApplyOverflow(height);
456.0     489 |     return (
456.0   > 490 |       <div
456.0         |       ^^^^
456.0   > 491 |         className={className}
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 492 |         style={{
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 493 |           height,
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 494 |           ...(shouldApplyOverflow
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 495 |             ? {
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 496 |                 display: 'block',
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 497 |                 boxSizing: 'border-box',
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 498 |                 overflowX: 'hidden',
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 499 |                 overflowY: 'auto',
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 500 |                 width: '100%',
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 501 |               }
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 502 |             : {}),
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 503 |         }}
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 504 |       >
456.0         | ^^^^^^^^
456.0     505 |         <div className="text-container">
456.0     506 |           {this.renderFallbackWarning()}
456.0     507 |           {this.renderMetricName((metricNameFontSize || 0) * height)}
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BigNumber/BigNumberViz.tsx:505:9
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     503 |         }}
456.0     504 |       >
456.0   > 505 |         <div className="text-container">
456.0         |         ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0     506 |           {this.renderFallbackWarning()}
456.0     507 |           {this.renderMetricName((metricNameFontSize || 0) * height)}
456.0     508 |           {this.renderKicker((kickerFontSize || 0) * height)}
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BigNumber/BigNumberWithTrendline/controlPanel.tsx:186:11
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     184 |         // eslint-disable-next-line react/jsx-key
456.0     185 |         [
456.0   > 186 |           <ControlSubSectionHeader>
456.0         |           ^^^^^^^^^^^^^^^^^^^^^^^^^
456.0     187 |             {t('Rolling Window')}
456.0     188 |           </ControlSubSectionHeader>,
456.0     189 |         ],
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BigNumber/BigNumberWithTrendline/controlPanel.tsx:242:10
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     240 |           },
456.0     241 |         ],
456.0   > 242 |         [<ControlSubSectionHeader>{t('Resample')}</ControlSubSectionHeader>],
456.0         |          ^^^^^^^^^^^^^^^^^^^^^^^^^
456.0     243 |         [
456.0     244 |           {
456.0     245 |             name: 'resample_rule',
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BigNumber/BigNumberWithTrendline/index.ts:20:26
456.0 TS6142: Module './controlPanel' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/BigNumber/BigNumberWithTrendline/controlPanel.tsx', but '--jsx' is not set.
456.0     18 |  */
456.0     19 | import { t, Behavior } from '@superset-ui/core';
456.0   > 20 | import controlPanel from './controlPanel';
456.0        |                          ^^^^^^^^^^^^^^^^
456.0     21 | import transformProps from './transformProps';
456.0     22 | import buildQuery from './buildQuery';
456.0     23 | import example from './images/Big_Number_Trendline.jpg';
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BigNumber/BigNumberWithTrendline/index.ts:57:31
456.0 TS6142: Module '../BigNumberViz' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/BigNumber/BigNumberViz.tsx', but '--jsx' is not set.
456.0     55 |   constructor() {
456.0     56 |     super({
456.0   > 57 |       loadChart: () => import('../BigNumberViz'),
456.0        |                               ^^^^^^^^^^^^^^^^^
456.0     58 |       metadata,
456.0     59 |       buildQuery,
456.0     60 |       transformProps,
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BigNumber/BigNumberWithTrendline/transformProps.test.ts:19:10
456.0 TS2305: Module '"@superset-ui/core"' has no exported member 'GenericDataType'.
456.0     17 |  * under the License.
456.0     18 |  */
456.0   > 19 | import { GenericDataType } from '@superset-ui/core';
456.0        |          ^^^^^^^^^^^^^^^
456.0     20 | import transformProps from './transformProps';
456.0     21 | import { BigNumberWithTrendlineChartProps, BigNumberDatum } from '../types';
456.0     22 |
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BigNumber/BigNumberWithTrendline/transformProps.ts:23:3
456.0 TS2305: Module '"@superset-ui/core"' has no exported member 'GenericDataType'.
456.0     21 |   getNumberFormatter,
456.0     22 |   NumberFormats,
456.0   > 23 |   GenericDataType,
456.0        |   ^^^^^^^^^^^^^^^
456.0     24 |   getMetricLabel,
456.0     25 |   getXAxisLabel,
456.0     26 |   Metric,
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BigNumber/BigNumberWithTrendline/transformProps.ts:252:32
456.0 TS2339: Property 'colors' does not exist on type 'SupersetTheme'.
456.0     250 |                 {
456.0     251 |                   offset: 1,
456.0   > 252 |                   color: theme.colors.grayscale.light5,
456.0         |                                ^^^^^^
456.0     253 |                 },
456.0     254 |               ]),
456.0     255 |             },
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BigNumber/utils.ts:20:8
456.0 TS1259: Module '"/app/superset-frontend/node_modules/dayjs/index"' can only be default-imported using the 'esModuleInterop' flag
456.0     18 |  */
456.0     19 |
456.0   > 20 | import dayjs from 'dayjs';
456.0        |        ^^^^^
456.0     21 | import utc from 'dayjs/plugin/utc';
456.0     22 | import {
456.0     23 |   getTimeFormatter,
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BigNumber/utils.ts:21:8
456.0 TS1259: Module '"/app/superset-frontend/node_modules/dayjs/plugin/utc"' can only be default-imported using the 'esModuleInterop' flag
456.0     19 |
456.0     20 | import dayjs from 'dayjs';
456.0   > 21 | import utc from 'dayjs/plugin/utc';
456.0        |        ^^^
456.0     22 | import {
456.0     23 |   getTimeFormatter,
456.0     24 |   getTimeFormatterForGranularity,
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BoxPlot/EchartsBoxPlot.tsx:19:20
456.0 TS6142: Module '../components/Echart' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/components/Echart.tsx', but '--jsx' is not set.
456.0     17 |  * under the License.
456.0     18 |  */
456.0   > 19 | import Echart from '../components/Echart';
456.0        |                    ^^^^^^^^^^^^^^^^^^^^^^
456.0     20 | import { allEventHandlers } from '../utils/eventHandlers';
456.0     21 | import { BoxPlotChartTransformedProps } from './types';
456.0     22 |
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BoxPlot/EchartsBoxPlot.tsx:29:5
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     27 |
456.0     28 |   return (
456.0   > 29 |     <Echart
456.0        |     ^^^^^^^
456.0   > 30 |       refs={refs}
456.0        | ^^^^^^^^^^^^^^^^^
456.0   > 31 |       height={height}
456.0        | ^^^^^^^^^^^^^^^^^
456.0   > 32 |       width={width}
456.0        | ^^^^^^^^^^^^^^^^^
456.0   > 33 |       echartOptions={echartOptions}
456.0        | ^^^^^^^^^^^^^^^^^
456.0   > 34 |       eventHandlers={eventHandlers}
456.0        | ^^^^^^^^^^^^^^^^^
456.0   > 35 |       selectedValues={selectedValues}
456.0        | ^^^^^^^^^^^^^^^^^
456.0   > 36 |     />
456.0        | ^^^^^^^
456.0     37 |   );
456.0     38 | }
456.0     39 |
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/BoxPlot/index.ts:46:31
456.0 TS6142: Module './EchartsBoxPlot' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/BoxPlot/EchartsBoxPlot.tsx', but '--jsx' is not set.
456.0     44 |       buildQuery,
456.0     45 |       controlPanel,
456.0   > 46 |       loadChart: () => import('./EchartsBoxPlot'),
456.0        |                               ^^^^^^^^^^^^^^^^^^
456.0     47 |       metadata: {
456.0     48 |         behaviors: [
456.0     49 |           Behavior.InteractiveChart,
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Bubble/controlPanel.tsx:35:8
456.0 TS6142: Module '../controls' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/controls.tsx', but '--jsx' is not set.
456.0     33 |   xAxisLabelRotation,
456.0     34 |   xAxisLabelInterval,
456.0   > 35 | } from '../controls';
456.0        |        ^^^^^^^^^^^^^
456.0     36 | import { defaultYAxis } from '../defaults';
456.0     37 |
456.0     38 | const { logAxis, truncateYAxis, yAxisBounds, opacity } = DEFAULT_FORM_DATA;
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Bubble/EchartsBubble.tsx:20:20
456.0 TS6142: Module '../components/Echart' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/components/Echart.tsx', but '--jsx' is not set.
456.0     18 |  */
456.0     19 | import { BubbleChartTransformedProps } from './types';
456.0   > 20 | import Echart from '../components/Echart';
456.0        |                    ^^^^^^^^^^^^^^^^^^^^^^
456.0     21 |
456.0     22 | export default function EchartsBubble(props: BubbleChartTransformedProps) {
456.0     23 |   const { height, width, echartOptions, refs } = props;
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Bubble/EchartsBubble.tsx:25:5
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     23 |   const { height, width, echartOptions, refs } = props;
456.0     24 |   return (
456.0   > 25 |     <Echart
456.0        |     ^^^^^^^
456.0   > 26 |       height={height}
456.0        | ^^^^^^^^^^^^^^^^^^^^^
456.0   > 27 |       width={width}
456.0        | ^^^^^^^^^^^^^^^^^^^^^
456.0   > 28 |       echartOptions={echartOptions}
456.0        | ^^^^^^^^^^^^^^^^^^^^^
456.0   > 29 |       refs={refs}
456.0        | ^^^^^^^^^^^^^^^^^^^^^
456.0   > 30 |     />
456.0        | ^^^^^^^
456.0     31 |   );
456.0     32 | }
456.0     33 |
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Bubble/index.ts:23:26
456.0 TS6142: Module './controlPanel' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/Bubble/controlPanel.tsx', but '--jsx' is not set.
456.0     21 | import transformProps from './transformProps';
456.0     22 | import buildQuery from './buildQuery';
456.0   > 23 | import controlPanel from './controlPanel';
456.0        |                          ^^^^^^^^^^^^^^^^
456.0     24 | import example1 from './images/example1.png';
456.0     25 | import example2 from './images/example2.png';
456.0     26 | import { EchartsBubbleChartProps, EchartsBubbleFormData } from './types';
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Bubble/index.ts:37:31
456.0 TS6142: Module './EchartsBubble' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/Bubble/EchartsBubble.tsx', but '--jsx' is not set.
456.0     35 |       buildQuery,
456.0     36 |       controlPanel,
456.0   > 37 |       loadChart: () => import('./EchartsBubble'),
456.0        |                               ^^^^^^^^^^^^^^^^^
456.0     38 |       metadata: new ChartMetadata({
456.0     39 |         category: t('Correlation'),
456.0     40 |         credits: ['https://echarts.apache.org'],
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/components/Echart.tsx:263:10
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     261 |   }, [width, height, handleSizeChange]);
456.0     262 |
456.0   > 263 |   return <Styles ref={divRef} height={height} width={width} />;
456.0         |          ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0     264 | }
456.0     265 |
456.0     266 | export default forwardRef(Echart);
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/components/ExtraControls.tsx:104:5
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     102 |
456.0     103 |   return (
456.0   > 104 |     <ExtraControlsWrapper>
456.0         |     ^^^^^^^^^^^^^^^^^^^^^^
456.0     105 |       <RadioButtonControl
456.0     106 |         options={extraControlsOptions}
456.0     107 |         onChange={extraControlsHandler}
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/components/ExtraControls.tsx:105:7
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     103 |   return (
456.0     104 |     <ExtraControlsWrapper>
456.0   > 105 |       <RadioButtonControl
456.0         |       ^^^^^^^^^^^^^^^^^^^
456.0   > 106 |         options={extraControlsOptions}
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 107 |         onChange={extraControlsHandler}
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 108 |         value={extraValue}
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 109 |       />
456.0         | ^^^^^^^^^
456.0     110 |     </ExtraControlsWrapper>
456.0     111 |   );
456.0     112 | }
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/controls.tsx:100:4
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0      98 |
456.0      99 | export const legendSection: ControlSetRow[] = [
456.0   > 100 |   [<ControlSubSectionHeader>{t('Legend')}</ControlSubSectionHeader>],
456.0         |    ^^^^^^^^^^^^^^^^^^^^^^^^^
456.0     101 |   [showLegendControl],
456.0     102 |   [legendTypeControl],
456.0     103 |   [legendOrientationControl],
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/controls.tsx:243:4
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     241 |
456.0     242 | export const richTooltipSection: ControlSetRow[] = [
456.0   > 243 |   [<ControlSubSectionHeader>{t('Tooltip')}</ControlSubSectionHeader>],
456.0         |    ^^^^^^^^^^^^^^^^^^^^^^^^^
456.0     244 |   [richTooltipControl],
456.0     245 |   [tooltipTotalControl],
456.0     246 |   [tooltipPercentageControl],
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/controls.tsx:313:4
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     311 |
456.0     312 | export const seriesOrderSection: ControlSetRow[] = [
456.0   > 313 |   [<ControlSubSectionHeader>{t('Series Order')}</ControlSubSectionHeader>],
456.0         |    ^^^^^^^^^^^^^^^^^^^^^^^^^
456.0     314 |   [sortSeriesType],
456.0     315 |   [sortSeriesAscending],
456.0     316 | ];
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Funnel/controlPanel.tsx:35:31
456.0 TS6142: Module '../controls' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/controls.tsx', but '--jsx' is not set.
456.0     33 |   PercentCalcType,
456.0     34 | } from './types';
456.0   > 35 | import { legendSection } from '../controls';
456.0        |                               ^^^^^^^^^^^^^
456.0     36 |
456.0     37 | const { labelType, numberFormat, showLabels, defaultTooltipLabel } =
456.0     38 |   DEFAULT_FORM_DATA;
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Funnel/controlPanel.tsx:101:10
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0      99 |         ...funnelLegendSection,
456.0     100 |         // eslint-disable-next-line react/jsx-key
456.0   > 101 |         [<ControlSubSectionHeader>{t('Labels')}</ControlSubSectionHeader>],
456.0         |          ^^^^^^^^^^^^^^^^^^^^^^^^^
456.0     102 |         [
456.0     103 |           {
456.0     104 |             name: 'label_type',
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Funnel/EchartsFunnel.tsx:20:20
456.0 TS6142: Module '../components/Echart' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/components/Echart.tsx', but '--jsx' is not set.
456.0     18 |  */
456.0     19 | import { FunnelChartTransformedProps } from './types';
456.0   > 20 | import Echart from '../components/Echart';
456.0        |                    ^^^^^^^^^^^^^^^^^^^^^^
456.0     21 | import { allEventHandlers } from '../utils/eventHandlers';
456.0     22 |
456.0     23 | export default function EchartsFunnel(props: FunnelChartTransformedProps) {
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Funnel/EchartsFunnel.tsx:29:5
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     27 |
456.0     28 |   return (
456.0   > 29 |     <Echart
456.0        |     ^^^^^^^
456.0   > 30 |       refs={refs}
456.0        | ^^^^^^^^^^^^^^^^^
456.0   > 31 |       height={height}
456.0        | ^^^^^^^^^^^^^^^^^
456.0   > 32 |       width={width}
456.0        | ^^^^^^^^^^^^^^^^^
456.0   > 33 |       echartOptions={echartOptions}
456.0        | ^^^^^^^^^^^^^^^^^
456.0   > 34 |       eventHandlers={eventHandlers}
456.0        | ^^^^^^^^^^^^^^^^^
456.0   > 35 |       selectedValues={selectedValues}
456.0        | ^^^^^^^^^^^^^^^^^
456.0   > 36 |     />
456.0        | ^^^^^^^
456.0     37 |   );
456.0     38 | }
456.0     39 |
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Funnel/index.ts:21:26
456.0 TS6142: Module './controlPanel' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/Funnel/controlPanel.tsx', but '--jsx' is not set.
456.0     19 | import { Behavior, t } from '@superset-ui/core';
456.0     20 | import buildQuery from './buildQuery';
456.0   > 21 | import controlPanel from './controlPanel';
456.0        |                          ^^^^^^^^^^^^^^^^
456.0     22 | import transformProps from './transformProps';
456.0     23 | import thumbnail from './images/thumbnail.png';
456.0     24 | import example from './images/example.jpg';
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Funnel/index.ts:46:31
456.0 TS6142: Module './EchartsFunnel' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/Funnel/EchartsFunnel.tsx', but '--jsx' is not set.
456.0     44 |       buildQuery,
456.0     45 |       controlPanel,
456.0   > 46 |       loadChart: () => import('./EchartsFunnel'),
456.0        |                               ^^^^^^^^^^^^^^^^^
456.0     47 |       metadata: {
456.0     48 |         behaviors: [
456.0     49 |           Behavior.InteractiveChart,
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Gauge/controlPanel.tsx:51:28
456.0 TS2802: Type 'IterableIterator<number>' can only be iterated through when using the '--downlevelIteration' flag or with a '--target' of 'es2015' or higher.
456.0     49 |             config: {
456.0     50 |               ...sharedControls.row_limit,
456.0   > 51 |               choices: [...Array(10).keys()].map(n => n + 1),
456.0        |                            ^^^^^^^^^^^^^^^^
456.0     52 |               default: DEFAULT_FORM_DATA.rowLimit,
456.0     53 |             },
456.0     54 |           },
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Gauge/controlPanel.tsx:63:10
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     61 |       expanded: true,
456.0     62 |       controlSetRows: [
456.0   > 63 |         [<ControlSubSectionHeader>{t('General')}</ControlSubSectionHeader>],
456.0        |          ^^^^^^^^^^^^^^^^^^^^^^^^^
456.0     64 |         [
456.0     65 |           {
456.0     66 |             name: 'min_val',
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Gauge/controlPanel.tsx:213:10
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     211 |           },
456.0     212 |         ],
456.0   > 213 |         [<ControlSubSectionHeader>{t('Axis')}</ControlSubSectionHeader>],
456.0         |          ^^^^^^^^^^^^^^^^^^^^^^^^^
456.0     214 |         [
456.0     215 |           {
456.0     216 |             name: 'show_axis_tick',
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Gauge/controlPanel.tsx:252:10
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     250 |           },
456.0     251 |         ],
456.0   > 252 |         [<ControlSubSectionHeader>{t('Progress')}</ControlSubSectionHeader>],
456.0         |          ^^^^^^^^^^^^^^^^^^^^^^^^^
456.0     253 |         [
456.0     254 |           {
456.0     255 |             name: 'show_progress',
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Gauge/controlPanel.tsx:293:10
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     291 |           },
456.0     292 |         ],
456.0   > 293 |         [<ControlSubSectionHeader>{t('Intervals')}</ControlSubSectionHeader>],
456.0         |          ^^^^^^^^^^^^^^^^^^^^^^^^^
456.0     294 |         [
456.0     295 |           {
456.0     296 |             name: 'intervals',
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Gauge/EchartsGauge.tsx:20:20
456.0 TS6142: Module '../components/Echart' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/components/Echart.tsx', but '--jsx' is not set.
456.0     18 |  */
456.0     19 | import { GaugeChartTransformedProps } from './types';
456.0   > 20 | import Echart from '../components/Echart';
456.0        |                    ^^^^^^^^^^^^^^^^^^^^^^
456.0     21 | import { allEventHandlers } from '../utils/eventHandlers';
456.0     22 |
456.0     23 | export default function EchartsGauge(props: GaugeChartTransformedProps) {
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Gauge/EchartsGauge.tsx:29:5
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     27 |
456.0     28 |   return (
456.0   > 29 |     <Echart
456.0        |     ^^^^^^^
456.0   > 30 |       refs={refs}
456.0        | ^^^^^^^^^^^^^^^^^
456.0   > 31 |       height={height}
456.0        | ^^^^^^^^^^^^^^^^^
456.0   > 32 |       width={width}
456.0        | ^^^^^^^^^^^^^^^^^
456.0   > 33 |       echartOptions={echartOptions}
456.0        | ^^^^^^^^^^^^^^^^^
456.0   > 34 |       eventHandlers={eventHandlers}
456.0        | ^^^^^^^^^^^^^^^^^
456.0   > 35 |       selectedValues={selectedValues}
456.0        | ^^^^^^^^^^^^^^^^^
456.0   > 36 |     />
456.0        | ^^^^^^^
456.0     37 |   );
456.0     38 | }
456.0     39 |
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Gauge/index.ts:20:26
456.0 TS6142: Module './controlPanel' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/Gauge/controlPanel.tsx', but '--jsx' is not set.
456.0     18 |  */
456.0     19 | import { t, Behavior } from '@superset-ui/core';
456.0   > 20 | import controlPanel from './controlPanel';
456.0        |                          ^^^^^^^^^^^^^^^^
456.0     21 | import transformProps from './transformProps';
456.0     22 | import thumbnail from './images/thumbnail.png';
456.0     23 | import example1 from './images/example1.jpg';
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Gauge/index.ts:37:31
456.0 TS6142: Module './EchartsGauge' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/Gauge/EchartsGauge.tsx', but '--jsx' is not set.
456.0     35 |       buildQuery,
456.0     36 |       controlPanel,
456.0   > 37 |       loadChart: () => import('./EchartsGauge'),
456.0        |                               ^^^^^^^^^^^^^^^^
456.0     38 |       metadata: {
456.0     39 |         behaviors: [
456.0     40 |           Behavior.InteractiveChart,
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Graph/controlPanel.tsx:27:31
456.0 TS6142: Module '../controls' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/controls.tsx', but '--jsx' is not set.
456.0     25 | } from '@superset-ui/chart-controls';
456.0     26 | import { DEFAULT_FORM_DATA } from './types';
456.0   > 27 | import { legendSection } from '../controls';
456.0        |                               ^^^^^^^^^^^^^
456.0     28 |
456.0     29 | const requiredEntity = {
456.0     30 |   ...sharedControls.entity,
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Graph/controlPanel.tsx:100:10
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0      98 |         ['color_scheme'],
456.0      99 |         ...legendSection,
456.0   > 100 |         [<ControlSubSectionHeader>{t('Layout')}</ControlSubSectionHeader>],
456.0         |          ^^^^^^^^^^^^^^^^^^^^^^^^^
456.0     101 |         [
456.0     102 |           {
456.0     103 |             name: 'layout',
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Graph/EchartsGraph.tsx:25:20
456.0 TS6142: Module '../components/Echart' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/components/Echart.tsx', but '--jsx' is not set.
456.0     23 | } from '@superset-ui/core';
456.0     24 | import { EventHandlers } from '../types';
456.0   > 25 | import Echart from '../components/Echart';
456.0        |                    ^^^^^^^^^^^^^^^^^^^^^^
456.0     26 | import { GraphChartTransformedProps } from './types';
456.0     27 | import { formatSeriesName } from '../utils/series';
456.0     28 |
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Graph/EchartsGraph.tsx:172:5
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     170 |   };
456.0     171 |   return (
456.0   > 172 |     <Echart
456.0         |     ^^^^^^^
456.0   > 173 |       refs={refs}
456.0         | ^^^^^^^^^^^^^^^^^
456.0   > 174 |       height={height}
456.0         | ^^^^^^^^^^^^^^^^^
456.0   > 175 |       width={width}
456.0         | ^^^^^^^^^^^^^^^^^
456.0   > 176 |       echartOptions={echartOptions}
456.0         | ^^^^^^^^^^^^^^^^^
456.0   > 177 |       eventHandlers={eventHandlers}
456.0         | ^^^^^^^^^^^^^^^^^
456.0   > 178 |     />
456.0         | ^^^^^^^
456.0     179 |   );
456.0     180 | }
456.0     181 |
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Graph/index.ts:20:26
456.0 TS6142: Module './controlPanel' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/Graph/controlPanel.tsx', but '--jsx' is not set.
456.0     18 |  */
456.0     19 | import { Behavior, t } from '@superset-ui/core';
456.0   > 20 | import controlPanel from './controlPanel';
456.0        |                          ^^^^^^^^^^^^^^^^
456.0     21 | import transformProps from './transformProps';
456.0     22 | import thumbnail from './images/thumbnail.png';
456.0     23 | import example from './images/example.jpg';
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Graph/index.ts:32:31
456.0 TS6142: Module './EchartsGraph' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/Graph/EchartsGraph.tsx', but '--jsx' is not set.
456.0     30 |       buildQuery,
456.0     31 |       controlPanel,
456.0   > 32 |       loadChart: () => import('./EchartsGraph'),
456.0        |                               ^^^^^^^^^^^^^^^^
456.0     33 |       metadata: {
456.0     34 |         category: t('Flow'),
456.0     35 |         credits: ['https://echarts.apache.org'],
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Graph/transformProps.ts:299:28
456.0 TS2802: Type 'Set<string>' can only be iterated through when using the '--downlevelIteration' flag or with a '--target' of 'es2015' or higher.
456.0     297 |   });
456.0     298 |
456.0   > 299 |   const categoryList = [...categories];
456.0         |                            ^^^^^^^^^^
456.0     300 |   const series: GraphSeriesOption[] = [
456.0     301 |     {
456.0     302 |       zoom: DEFAULT_GRAPH_SERIES_OPTION.zoom,
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Heatmap/controlPanel.tsx:83:17
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     81 |               renderTrigger: false,
456.0     82 |               description: (
456.0   > 83 |                 <>
456.0        |                 ^^
456.0     84 |                   <div>
456.0     85 |                     {t(
456.0     86 |                       'Color will be shaded based the normalized (0% to 100%) value of a given cell against the other cells in the selected range: ',
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Heatmap/controlPanel.tsx:84:19
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     82 |               description: (
456.0     83 |                 <>
456.0   > 84 |                   <div>
456.0        |                   ^^^^^
456.0     85 |                     {t(
456.0     86 |                       'Color will be shaded based the normalized (0% to 100%) value of a given cell against the other cells in the selected range: ',
456.0     87 |                     )}
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Heatmap/controlPanel.tsx:89:19
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     87 |                     )}
456.0     88 |                   </div>
456.0   > 89 |                   <ul>
456.0        |                   ^^^^
456.0     90 |                     <li>{t('x: values are normalized within each column')}</li>
456.0     91 |                     <li>{t('y: values are normalized within each row')}</li>
456.0     92 |                     <li>
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Heatmap/controlPanel.tsx:90:21
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     88 |                   </div>
456.0     89 |                   <ul>
456.0   > 90 |                     <li>{t('x: values are normalized within each column')}</li>
456.0        |                     ^^^^
456.0     91 |                     <li>{t('y: values are normalized within each row')}</li>
456.0     92 |                     <li>
456.0     93 |                       {t(
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Heatmap/controlPanel.tsx:91:21
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     89 |                   <ul>
456.0     90 |                     <li>{t('x: values are normalized within each column')}</li>
456.0   > 91 |                     <li>{t('y: values are normalized within each row')}</li>
456.0        |                     ^^^^
456.0     92 |                     <li>
456.0     93 |                       {t(
456.0     94 |                         'heatmap: values are normalized across the entire heatmap',
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Heatmap/controlPanel.tsx:92:21
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     90 |                     <li>{t('x: values are normalized within each column')}</li>
456.0     91 |                     <li>{t('y: values are normalized within each row')}</li>
456.0   > 92 |                     <li>
456.0        |                     ^^^^
456.0     93 |                       {t(
456.0     94 |                         'heatmap: values are normalized across the entire heatmap',
456.0     95 |                       )}
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Heatmap/Heatmap.tsx:20:20
456.0 TS6142: Module '../components/Echart' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/components/Echart.tsx', but '--jsx' is not set.
456.0     18 |  */
456.0     19 | import { HeatmapTransformedProps } from './types';
456.0   > 20 | import Echart from '../components/Echart';
456.0        |                    ^^^^^^^^^^^^^^^^^^^^^^
456.0     21 |
456.0     22 | export default function Heatmap(props: HeatmapTransformedProps) {
456.0     23 |   const { height, width, echartOptions, refs } = props;
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Heatmap/Heatmap.tsx:25:5
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     23 |   const { height, width, echartOptions, refs } = props;
456.0     24 |   return (
456.0   > 25 |     <Echart
456.0        |     ^^^^^^^
456.0   > 26 |       refs={refs}
456.0        | ^^^^^^^^^^^^^^^^^
456.0   > 27 |       height={height}
456.0        | ^^^^^^^^^^^^^^^^^
456.0   > 28 |       width={width}
456.0        | ^^^^^^^^^^^^^^^^^
456.0   > 29 |       echartOptions={echartOptions}
456.0        | ^^^^^^^^^^^^^^^^^
456.0   > 30 |     />
456.0        | ^^^^^^^
456.0     31 |   );
456.0     32 | }
456.0     33 |
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Heatmap/index.ts:26:26
456.0 TS6142: Module './controlPanel' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/Heatmap/controlPanel.tsx', but '--jsx' is not set.
456.0     24 | import example3 from './images/example3.png';
456.0     25 | import thumbnail from './images/thumbnail.png';
456.0   > 26 | import controlPanel from './controlPanel';
456.0        |                          ^^^^^^^^^^^^^^^^
456.0     27 |
456.0     28 | const metadata = new ChartMetadata({
456.0     29 |   category: t('Correlation'),
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Heatmap/index.ts:50:31
456.0 TS6142: Module './Heatmap' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/Heatmap/Heatmap.tsx', but '--jsx' is not set.
456.0     48 |     super({
456.0     49 |       buildQuery,
456.0   > 50 |       loadChart: () => import('./Heatmap'),
456.0        |                               ^^^^^^^^^^^
456.0     51 |       metadata,
456.0     52 |       transformProps,
456.0     53 |       controlPanel,
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Heatmap/transformProps.ts:20:3
456.0 TS2305: Module '"@superset-ui/core"' has no exported member 'GenericDataType'.
456.0     18 |  */
456.0     19 | import {
456.0   > 20 |   GenericDataType,
456.0        |   ^^^^^^^^^^^^^^^
456.0     21 |   NumberFormats,
456.0     22 |   QueryFormColumn,
456.0     23 |   getColumnLabel,
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Heatmap/transformProps.ts:178:38
456.0 TS2339: Property 'colors' does not exist on type 'SupersetTheme'.
456.0     176 |       emphasis: {
456.0     177 |         itemStyle: {
456.0   > 178 |           borderColor: supersetTheme.colors.grayscale.light5,
456.0         |                                      ^^^^^^
456.0     179 |           shadowBlur: 10,
456.0     180 |           shadowColor: supersetTheme.colors.grayscale.dark2,
456.0     181 |         },
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Heatmap/transformProps.ts:180:38
456.0 TS2339: Property 'colors' does not exist on type 'SupersetTheme'.
456.0     178 |           borderColor: supersetTheme.colors.grayscale.light5,
456.0     179 |           shadowBlur: 10,
456.0   > 180 |           shadowColor: supersetTheme.colors.grayscale.dark2,
456.0         |                                      ^^^^^^
456.0     181 |         },
456.0     182 |       },
456.0     183 |     },
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Histogram/controlPanel.tsx:20:3
456.0 TS2305: Module '"@superset-ui/core"' has no exported member 'GenericDataType'.
456.0     18 |  */
456.0     19 | import {
456.0   > 20 |   GenericDataType,
456.0        |   ^^^^^^^^^^^^^^^
456.0     21 |   t,
456.0     22 |   validateInteger,
456.0     23 |   validateNonEmpty,
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Histogram/controlPanel.tsx:34:53
456.0 TS6142: Module '../controls' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/controls.tsx', but '--jsx' is not set.
456.0     32 |   D3_NUMBER_FORMAT_DESCRIPTION_VALUES_TEXT,
456.0     33 | } from '@superset-ui/chart-controls';
456.0   > 34 | import { showLegendControl, showValueControl } from '../controls';
456.0        |                                                     ^^^^^^^^^^^^^
456.0     35 |
456.0     36 | const config: ControlPanelConfig = {
456.0     37 |   controlPanelSections: [
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Histogram/Histogram.tsx:20:20
456.0 TS6142: Module '../components/Echart' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/components/Echart.tsx', but '--jsx' is not set.
456.0     18 |  */
456.0     19 | import { HistogramTransformedProps } from './types';
456.0   > 20 | import Echart from '../components/Echart';
456.0        |                    ^^^^^^^^^^^^^^^^^^^^^^
456.0     21 | import { EventHandlers } from '../types';
456.0     22 |
456.0     23 | export default function Histogram(props: HistogramTransformedProps) {
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Histogram/Histogram.tsx:52:5
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     50 |
456.0     51 |   return (
456.0   > 52 |     <Echart
456.0        |     ^^^^^^^
456.0   > 53 |       refs={refs}
456.0        | ^^^^^^^^^^^^^^^^^
456.0   > 54 |       height={height}
456.0        | ^^^^^^^^^^^^^^^^^
456.0   > 55 |       width={width}
456.0        | ^^^^^^^^^^^^^^^^^
456.0   > 56 |       echartOptions={echartOptions}
456.0        | ^^^^^^^^^^^^^^^^^
456.0   > 57 |       eventHandlers={eventHandlers}
456.0        | ^^^^^^^^^^^^^^^^^
456.0   > 58 |     />
456.0        | ^^^^^^^
456.0     59 |   );
456.0     60 | }
456.0     61 |
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Histogram/index.ts:22:26
456.0 TS6142: Module './controlPanel' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/Histogram/controlPanel.tsx', but '--jsx' is not set.
456.0     20 | import { ChartMetadata, ChartPlugin, t } from '@superset-ui/core';
456.0     21 | import buildQuery from './buildQuery';
456.0   > 22 | import controlPanel from './controlPanel';
456.0        |                          ^^^^^^^^^^^^^^^^
456.0     23 | import transformProps from './transformProps';
456.0     24 | import thumbnail from './images/thumbnail.png';
456.0     25 | import example1 from './images/example1.png';
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Histogram/index.ts:48:31
456.0 TS6142: Module './Histogram' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/Histogram/Histogram.tsx', but '--jsx' is not set.
456.0     46 |       buildQuery,
456.0     47 |       controlPanel,
456.0   > 48 |       loadChart: () => import('./Histogram'),
456.0        |                               ^^^^^^^^^^^^^
456.0     49 |       metadata: new ChartMetadata({
456.0     50 |         credits: ['https://echarts.apache.org'],
456.0     51 |         category: t('Distribution'),
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/MixedTimeseries/controlPanel.tsx:45:8
456.0 TS6142: Module '../controls' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/controls.tsx', but '--jsx' is not set.
456.0     43 |   xAxisLabelRotation,
456.0     44 |   xAxisLabelInterval,
456.0   > 45 | } from '../controls';
456.0        |        ^^^^^^^^^^^^^
456.0     46 |
456.0     47 | const {
456.0     48 |   area,
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/MixedTimeseries/controlPanel.tsx:141:6
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     139 | ): ControlSetRow[] {
456.0     140 |   return [
456.0   > 141 |     [<ControlSubSectionHeader>{label}</ControlSubSectionHeader>],
456.0         |      ^^^^^^^^^^^^^^^^^^^^^^^^^
456.0     142 |     [
456.0     143 |       {
456.0     144 |         name: `seriesType${controlSuffix}`,
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/MixedTimeseries/controlPanel.tsx:282:6
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     280 |       },
456.0     281 |     ],
456.0   > 282 |     [<ControlSubSectionHeader>{t('Series Order')}</ControlSubSectionHeader>],
456.0         |      ^^^^^^^^^^^^^^^^^^^^^^^^^
456.0     283 |     [
456.0     284 |       {
456.0     285 |         name: `sort_series_type${controlSuffix}`,
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/MixedTimeseries/controlPanel.tsx:369:10
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     367 |         [minorTicks],
456.0     368 |         ...legendSection,
456.0   > 369 |         [<ControlSubSectionHeader>{t('X Axis')}</ControlSubSectionHeader>],
456.0         |          ^^^^^^^^^^^^^^^^^^^^^^^^^
456.0     370 |         ['x_axis_time_format'],
456.0     371 |         [xAxisLabelRotation],
456.0     372 |         [xAxisLabelInterval],
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/MixedTimeseries/controlPanel.tsx:375:10
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     373 |         ...richTooltipSection,
456.0     374 |         // eslint-disable-next-line react/jsx-key
456.0   > 375 |         [<ControlSubSectionHeader>{t('Y Axis')}</ControlSubSectionHeader>],
456.0         |          ^^^^^^^^^^^^^^^^^^^^^^^^^
456.0     376 |         [
456.0     377 |           {
456.0     378 |             name: 'minorSplitLine',
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/MixedTimeseries/EchartsMixedTimeseries.tsx:30:20
456.0 TS6142: Module '../components/Echart' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/components/Echart.tsx', but '--jsx' is not set.
456.0     28 | } from '@superset-ui/core';
456.0     29 | import { EchartsMixedTimeseriesChartTransformedProps } from './types';
456.0   > 30 | import Echart from '../components/Echart';
456.0        |                    ^^^^^^^^^^^^^^^^^^^^^^
456.0     31 | import { EventHandlers } from '../types';
456.0     32 | import { formatSeriesName } from '../utils/series';
456.0     33 |
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/MixedTimeseries/EchartsMixedTimeseries.tsx:213:5
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     211 |
456.0     212 |   return (
456.0   > 213 |     <Echart
456.0         |     ^^^^^^^
456.0   > 214 |       refs={refs}
456.0         | ^^^^^^^^^^^^^^^^^
456.0   > 215 |       height={height}
456.0         | ^^^^^^^^^^^^^^^^^
456.0   > 216 |       width={width}
456.0         | ^^^^^^^^^^^^^^^^^
456.0   > 217 |       echartOptions={echartOptions}
456.0         | ^^^^^^^^^^^^^^^^^
456.0   > 218 |       eventHandlers={eventHandlers}
456.0         | ^^^^^^^^^^^^^^^^^
456.0   > 219 |       selectedValues={selectedValues}
456.0         | ^^^^^^^^^^^^^^^^^
456.0   > 220 |     />
456.0         | ^^^^^^^
456.0     221 |   );
456.0     222 | }
456.0     223 |
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/MixedTimeseries/index.ts:21:26
456.0 TS6142: Module './controlPanel' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/MixedTimeseries/controlPanel.tsx', but '--jsx' is not set.
456.0     19 | import { AnnotationType, Behavior, t } from '@superset-ui/core';
456.0     20 | import buildQuery from './buildQuery';
456.0   > 21 | import controlPanel from './controlPanel';
456.0        |                          ^^^^^^^^^^^^^^^^
456.0     22 | import transformProps from './transformProps';
456.0     23 | import thumbnail from './images/thumbnail.png';
456.0     24 | import example from './images/example.jpg';
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/MixedTimeseries/index.ts:49:31
456.0 TS6142: Module './EchartsMixedTimeseries' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/MixedTimeseries/EchartsMixedTimeseries.tsx', but '--jsx' is not set.
456.0     47 |       buildQuery,
456.0     48 |       controlPanel,
456.0   > 49 |       loadChart: () => import('./EchartsMixedTimeseries'),
456.0        |                               ^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0     50 |       metadata: {
456.0     51 |         behaviors: [
456.0     52 |           Behavior.InteractiveChart,
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/MixedTimeseries/transformProps.ts:28:3
456.0 TS2305: Module '"@superset-ui/core"' has no exported member 'GenericDataType'.
456.0     26 |   CurrencyFormatter,
456.0     27 |   ensureIsArray,
456.0   > 28 |   GenericDataType,
456.0        |   ^^^^^^^^^^^^^^^
456.0     29 |   getCustomFormatter,
456.0     30 |   getNumberFormatter,
456.0     31 |   getXAxisLabel,
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Pie/controlPanel.tsx:32:31
456.0 TS6142: Module '../controls' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/controls.tsx', but '--jsx' is not set.
456.0     30 | } from '@superset-ui/chart-controls';
456.0     31 | import { DEFAULT_FORM_DATA } from './types';
456.0   > 32 | import { legendSection } from '../controls';
456.0        |                               ^^^^^^^^^^^^^
456.0     33 |
456.0     34 | const {
456.0     35 |   donut,
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Pie/controlPanel.tsx:123:10
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     121 |         ...legendSection,
456.0     122 |         // eslint-disable-next-line react/jsx-key
456.0   > 123 |         [<ControlSubSectionHeader>{t('Labels')}</ControlSubSectionHeader>],
456.0         |          ^^^^^^^^^^^^^^^^^^^^^^^^^
456.0     124 |         [
456.0     125 |           {
456.0     126 |             name: 'label_type',
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Pie/controlPanel.tsx:250:10
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     248 |         ],
456.0     249 |         // eslint-disable-next-line react/jsx-key
456.0   > 250 |         [<ControlSubSectionHeader>{t('Pie shape')}</ControlSubSectionHeader>],
456.0         |          ^^^^^^^^^^^^^^^^^^^^^^^^^
456.0     251 |         [
456.0     252 |           {
456.0     253 |             name: 'outerRadius',
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Pie/EchartsPie.tsx:20:20
456.0 TS6142: Module '../components/Echart' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/components/Echart.tsx', but '--jsx' is not set.
456.0     18 |  */
456.0     19 | import { PieChartTransformedProps } from './types';
456.0   > 20 | import Echart from '../components/Echart';
456.0        |                    ^^^^^^^^^^^^^^^^^^^^^^
456.0     21 | import { allEventHandlers } from '../utils/eventHandlers';
456.0     22 |
456.0     23 | export default function EchartsPie(props: PieChartTransformedProps) {
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Pie/EchartsPie.tsx:29:5
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     27 |
456.0     28 |   return (
456.0   > 29 |     <Echart
456.0        |     ^^^^^^^
456.0   > 30 |       refs={refs}
456.0        | ^^^^^^^^^^^^^^^^^
456.0   > 31 |       height={height}
456.0        | ^^^^^^^^^^^^^^^^^
456.0   > 32 |       width={width}
456.0        | ^^^^^^^^^^^^^^^^^
456.0   > 33 |       echartOptions={echartOptions}
456.0        | ^^^^^^^^^^^^^^^^^
456.0   > 34 |       eventHandlers={eventHandlers}
456.0        | ^^^^^^^^^^^^^^^^^
456.0   > 35 |       selectedValues={selectedValues}
456.0        | ^^^^^^^^^^^^^^^^^
456.0   > 36 |     />
456.0        | ^^^^^^^
456.0     37 |   );
456.0     38 | }
456.0     39 |
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Pie/index.ts:21:26
456.0 TS6142: Module './controlPanel' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/Pie/controlPanel.tsx', but '--jsx' is not set.
456.0     19 | import { Behavior, t } from '@superset-ui/core';
456.0     20 | import buildQuery from './buildQuery';
456.0   > 21 | import controlPanel from './controlPanel';
456.0        |                          ^^^^^^^^^^^^^^^^
456.0     22 | import transformProps from './transformProps';
456.0     23 | import thumbnail from './images/thumbnail.png';
456.0     24 | import example1 from './images/Pie1.jpg';
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Pie/index.ts:49:31
456.0 TS6142: Module './EchartsPie' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/Pie/EchartsPie.tsx', but '--jsx' is not set.
456.0     47 |       buildQuery,
456.0     48 |       controlPanel,
456.0   > 49 |       loadChart: () => import('./EchartsPie'),
456.0        |                               ^^^^^^^^^^^^^^
456.0     50 |       metadata: {
456.0     51 |         behaviors: [
456.0     52 |           Behavior.InteractiveChart,
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Pie/transformProps.ts:223:24
456.0 TS2339: Property 'colors' does not exist on type 'SupersetTheme'.
456.0     221 |         value: otherSum,
456.0     222 |         itemStyle: {
456.0   > 223 |           color: theme.colors.grayscale.dark1,
456.0         |                        ^^^^^^
456.0     224 |           opacity:
456.0     225 |             filterState.selectedValues &&
456.0     226 |             !filterState.selectedValues.includes(otherName)
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Pie/transformProps.ts:325:34
456.0 TS2550: Property 'replaceAll' does not exist on type 'string'. Do you need to change your target library? Try changing the 'lib' compiler option to 'es2021' or later.
456.0     323 |
456.0     324 |     return Object.entries(items).reduce(
456.0   > 325 |       (acc, [key, value]) => acc.replaceAll(key, value),
456.0         |                                  ^^^^^^^^^^
456.0     326 |       template,
456.0     327 |     );
456.0     328 |   };
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Pie/transformProps.ts:371:18
456.0 TS2339: Property 'colors' does not exist on type 'SupersetTheme'.
456.0     369 |     formatter,
456.0     370 |     show: showLabels,
456.0   > 371 |     color: theme.colors.grayscale.dark2,
456.0         |                  ^^^^^^
456.0     372 |   };
456.0     373 |
456.0     374 |   const chartPadding = getChartPadding(
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Pie/transformProps.ts:406:34
456.0 TS2339: Property 'colors' does not exist on type 'SupersetTheme'.
456.0     404 |           show: true,
456.0     405 |           fontWeight: 'bold',
456.0   > 406 |           backgroundColor: theme.colors.grayscale.light5,
456.0         |                                  ^^^^^^
456.0     407 |         },
456.0     408 |       },
456.0     409 |       data: transformedData,
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Radar/controlPanel.tsx:21:3
456.0 TS2305: Module '"@superset-ui/core"' has no exported member 'GenericDataType'.
456.0     19 | import {
456.0     20 |   ChartDataResponseResult,
456.0   > 21 |   GenericDataType,
456.0        |   ^^^^^^^^^^^^^^^
456.0     22 |   QueryFormMetric,
456.0     23 |   t,
456.0     24 |   validateNumber,
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Radar/controlPanel.tsx:39:31
456.0 TS6142: Module '../controls' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/controls.tsx', but '--jsx' is not set.
456.0     37 | import { DEFAULT_FORM_DATA } from './types';
456.0     38 | import { LABEL_POSITION } from '../constants';
456.0   > 39 | import { legendSection } from '../controls';
456.0        |                               ^^^^^^^^^^^^^
456.0     40 |
456.0     41 | const { labelType, labelPosition, numberFormat, showLabels, isCircle } =
456.0     42 |   DEFAULT_FORM_DATA;
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Radar/controlPanel.tsx:102:10
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     100 |         ['color_scheme'],
456.0     101 |         ...legendSection,
456.0   > 102 |         [<ControlSubSectionHeader>{t('Labels')}</ControlSubSectionHeader>],
456.0         |          ^^^^^^^^^^^^^^^^^^^^^^^^^
456.0     103 |         [
456.0     104 |           {
456.0     105 |             name: 'show_labels',
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Radar/controlPanel.tsx:173:10
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     171 |           },
456.0     172 |         ],
456.0   > 173 |         [<ControlSubSectionHeader>{t('Radar')}</ControlSubSectionHeader>],
456.0         |          ^^^^^^^^^^^^^^^^^^^^^^^^^
456.0     174 |         [
456.0     175 |           {
456.0     176 |             name: 'column_config',
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Radar/EchartsRadar.tsx:20:20
456.0 TS6142: Module '../components/Echart' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/components/Echart.tsx', but '--jsx' is not set.
456.0     18 |  */
456.0     19 | import { RadarChartTransformedProps } from './types';
456.0   > 20 | import Echart from '../components/Echart';
456.0        |                    ^^^^^^^^^^^^^^^^^^^^^^
456.0     21 | import { allEventHandlers } from '../utils/eventHandlers';
456.0     22 |
456.0     23 | export default function EchartsRadar(props: RadarChartTransformedProps) {
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Radar/EchartsRadar.tsx:28:5
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     26 |
456.0     27 |   return (
456.0   > 28 |     <Echart
456.0        |     ^^^^^^^
456.0   > 29 |       refs={refs}
456.0        | ^^^^^^^^^^^^^^^^^
456.0   > 30 |       height={height}
456.0        | ^^^^^^^^^^^^^^^^^
456.0   > 31 |       width={width}
456.0        | ^^^^^^^^^^^^^^^^^
456.0   > 32 |       echartOptions={echartOptions}
456.0        | ^^^^^^^^^^^^^^^^^
456.0   > 33 |       eventHandlers={eventHandlers}
456.0        | ^^^^^^^^^^^^^^^^^
456.0   > 34 |       selectedValues={selectedValues}
456.0        | ^^^^^^^^^^^^^^^^^
456.0   > 35 |     />
456.0        | ^^^^^^^
456.0     36 |   );
456.0     37 | }
456.0     38 |
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Radar/index.ts:22:26
456.0 TS6142: Module './controlPanel' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/Radar/controlPanel.tsx', but '--jsx' is not set.
456.0     20 | import { Behavior, t } from '@superset-ui/core';
456.0     21 | import buildQuery from './buildQuery';
456.0   > 22 | import controlPanel from './controlPanel';
456.0        |                          ^^^^^^^^^^^^^^^^
456.0     23 | import transformProps from './transformProps';
456.0     24 | import thumbnail from './images/thumbnail.png';
456.0     25 | import example1 from './images/example1.jpg';
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Radar/index.ts:48:31
456.0 TS6142: Module './EchartsRadar' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/Radar/EchartsRadar.tsx', but '--jsx' is not set.
456.0     46 |       buildQuery,
456.0     47 |       controlPanel,
456.0   > 48 |       loadChart: () => import('./EchartsRadar'),
456.0        |                               ^^^^^^^^^^^^^^^^
456.0     49 |       metadata: {
456.0     50 |         behaviors: [
456.0     51 |           Behavior.InteractiveChart,
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Sankey/index.ts:22:26
456.0 TS6142: Module './controlPanel' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/Sankey/controlPanel.tsx', but '--jsx' is not set.
456.0     20 | import { ChartMetadata, ChartPlugin, t } from '@superset-ui/core';
456.0     21 | import buildQuery from './buildQuery';
456.0   > 22 | import controlPanel from './controlPanel';
456.0        |                          ^^^^^^^^^^^^^^^^
456.0     23 | import transformProps from './transformProps';
456.0     24 | import thumbnail from './images/thumbnail.png';
456.0     25 | import example1 from './images/example1.png';
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Sankey/index.ts:48:31
456.0 TS6142: Module './Sankey' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/Sankey/Sankey.tsx', but '--jsx' is not set.
456.0     46 |       buildQuery,
456.0     47 |       controlPanel,
456.0   > 48 |       loadChart: () => import('./Sankey'),
456.0        |                               ^^^^^^^^^^
456.0     49 |       metadata: new ChartMetadata({
456.0     50 |         credits: ['https://echarts.apache.org'],
456.0     51 |         category: t('Flow'),
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Sankey/Sankey.tsx:20:20
456.0 TS6142: Module '../components/Echart' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/components/Echart.tsx', but '--jsx' is not set.
456.0     18 |  */
456.0     19 | import { SankeyTransformedProps } from './types';
456.0   > 20 | import Echart from '../components/Echart';
456.0        |                    ^^^^^^^^^^^^^^^^^^^^^^
456.0     21 |
456.0     22 | export default function Sankey(props: SankeyTransformedProps) {
456.0     23 |   const { height, width, echartOptions, refs } = props;
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Sankey/Sankey.tsx:26:5
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     24 |
456.0     25 |   return (
456.0   > 26 |     <Echart
456.0        |     ^^^^^^^
456.0   > 27 |       refs={refs}
456.0        | ^^^^^^^^^^^^^^^^^
456.0   > 28 |       height={height}
456.0        | ^^^^^^^^^^^^^^^^^
456.0   > 29 |       width={width}
456.0        | ^^^^^^^^^^^^^^^^^
456.0   > 30 |       echartOptions={echartOptions}
456.0        | ^^^^^^^^^^^^^^^^^
456.0   > 31 |     />
456.0        | ^^^^^^^
456.0     32 |   );
456.0     33 | }
456.0     34 |
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/controlPanel.tsx:54:10
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     52 |         ['color_scheme'],
456.0     53 |         ['linear_color_scheme'],
456.0   > 54 |         [<ControlSubSectionHeader>{t('Labels')}</ControlSubSectionHeader>],
456.0        |          ^^^^^^^^^^^^^^^^^^^^^^^^^
456.0     55 |         [
456.0     56 |           {
456.0     57 |             name: 'show_labels',
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/EchartsSunburst.tsx:27:20
456.0 TS6142: Module '../components/Echart' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/components/Echart.tsx', but '--jsx' is not set.
456.0     25 | } from '@superset-ui/core';
456.0     26 | import { SunburstTransformedProps } from './types';
456.0   > 27 | import Echart from '../components/Echart';
456.0        |                    ^^^^^^^^^^^^^^^^^^^^^^
456.0     28 | import { EventHandlers, TreePathInfo } from '../types';
456.0     29 | import { formatSeriesName } from '../utils/series';
456.0     30 |
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/EchartsSunburst.tsx:155:5
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     153 |
456.0     154 |   return (
456.0   > 155 |     <Echart
456.0         |     ^^^^^^^
456.0   > 156 |       refs={refs}
456.0         | ^^^^^^^^^^^^^^^^^
456.0   > 157 |       height={height}
456.0         | ^^^^^^^^^^^^^^^^^
456.0   > 158 |       width={width}
456.0         | ^^^^^^^^^^^^^^^^^
456.0   > 159 |       echartOptions={echartOptions}
456.0         | ^^^^^^^^^^^^^^^^^
456.0   > 160 |       eventHandlers={eventHandlers}
456.0         | ^^^^^^^^^^^^^^^^^
456.0   > 161 |       selectedValues={selectedValues}
456.0         | ^^^^^^^^^^^^^^^^^
456.0   > 162 |     />
456.0         | ^^^^^^^
456.0     163 |   );
456.0     164 | }
456.0     165 |
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/index.ts:22:26
456.0 TS6142: Module './controlPanel' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/Sunburst/controlPanel.tsx', but '--jsx' is not set.
456.0     20 | import transformProps from './transformProps';
456.0     21 | import thumbnail from './images/thumbnail.png';
456.0   > 22 | import controlPanel from './controlPanel';
456.0        |                          ^^^^^^^^^^^^^^^^
456.0     23 | import buildQuery from './buildQuery';
456.0     24 | import example1 from './images/Sunburst1.png';
456.0     25 | import example2 from './images/Sunburst2.png';
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/index.ts:33:31
456.0 TS6142: Module './EchartsSunburst' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/Sunburst/EchartsSunburst.tsx', but '--jsx' is not set.
456.0     31 |       buildQuery,
456.0     32 |       controlPanel,
456.0   > 33 |       loadChart: () => import('./EchartsSunburst'),
456.0        |                               ^^^^^^^^^^^^^^^^^^^
456.0     34 |       metadata: {
456.0     35 |         behaviors: [
456.0     36 |           Behavior.InteractiveChart,
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/transformProps.ts:135:6
456.0 TS2550: Property 'replaceAll' does not exist on type 'string'. Do you need to change your target library? Try changing the 'lib' compiler option to 'es2021' or later.
456.0     133 |   const title = (node.name || NULL_STRING)
456.0     134 |     .toString()
456.0   > 135 |     .replaceAll('<', '&lt;')
456.0         |      ^^^^^^^^^^
456.0     136 |     .replaceAll('>', '&gt;');
456.0     137 |   const rows = [[t('% of total'), absolutePercentage]];
456.0     138 |   if (parentNode) {
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Area/controlPanel.tsx:26:8
456.0 TS6142: Module '../../controls' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/controls.tsx', but '--jsx' is not set.
456.0     24 |   xAxisBounds,
456.0     25 |   minorTicks,
456.0   > 26 | } from '../../controls';
456.0        |        ^^^^^^^^^^^^^^^^
456.0     27 | import { AreaChartStackControlOptions } from '../../constants';
456.0     28 |
456.0     29 | const {
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Area/controlPanel.tsx:202:10
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     200 |         ],
456.0     201 |         ...legendSection,
456.0   > 202 |         [<ControlSubSectionHeader>{t('X Axis')}</ControlSubSectionHeader>],
456.0         |          ^^^^^^^^^^^^^^^^^^^^^^^^^
456.0     203 |         [
456.0     204 |           {
456.0     205 |             name: 'x_axis_time_format',
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Area/controlPanel.tsx:216:10
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     214 |         [xAxisLabelInterval],
456.0     215 |         ...richTooltipSection,
456.0   > 216 |         [<ControlSubSectionHeader>{t('Y Axis')}</ControlSubSectionHeader>],
456.0         |          ^^^^^^^^^^^^^^^^^^^^^^^^^
456.0     217 |         ['y_axis_format'],
456.0     218 |         ['currency_format'],
456.0     219 |         [
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Area/index.ts:21:26
456.0 TS6142: Module './controlPanel' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/Timeseries/Area/controlPanel.tsx', but '--jsx' is not set.
456.0     19 | import { t, AnnotationType, Behavior } from '@superset-ui/core';
456.0     20 | import buildQuery from '../buildQuery';
456.0   > 21 | import controlPanel from './controlPanel';
456.0        |                          ^^^^^^^^^^^^^^^^
456.0     22 | import transformProps from '../transformProps';
456.0     23 | import thumbnail from './images/thumbnail.png';
456.0     24 | import {
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Area/index.ts:45:31
456.0 TS6142: Module '../EchartsTimeseries' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/Timeseries/EchartsTimeseries.tsx', but '--jsx' is not set.
456.0     43 |       buildQuery,
456.0     44 |       controlPanel,
456.0   > 45 |       loadChart: () => import('../EchartsTimeseries'),
456.0        |                               ^^^^^^^^^^^^^^^^^^^^^^
456.0     46 |       metadata: {
456.0     47 |         behaviors: [
456.0     48 |           Behavior.InteractiveChart,
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/EchartsTimeseries.tsx:34:20
456.0 TS6142: Module '../components/Echart' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/components/Echart.tsx', but '--jsx' is not set.
456.0     32 | import type ComponentModel from 'echarts/types/src/model/Component';
456.0     33 | import { EchartsHandler, EventHandlers } from '../types';
456.0   > 34 | import Echart from '../components/Echart';
456.0        |                    ^^^^^^^^^^^^^^^^^^^^^^
456.0     35 | import { TimeseriesChartTransformedProps } from './types';
456.0     36 | import { formatSeriesName } from '../utils/series';
456.0     37 | import { ExtraControls } from '../components/ExtraControls';
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/EchartsTimeseries.tsx:37:31
456.0 TS6142: Module '../components/ExtraControls' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/components/ExtraControls.tsx', but '--jsx' is not set.
456.0     35 | import { TimeseriesChartTransformedProps } from './types';
456.0     36 | import { formatSeriesName } from '../utils/series';
456.0   > 37 | import { ExtraControls } from '../components/ExtraControls';
456.0        |                               ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0     38 |
456.0     39 | const TIMER_DURATION = 300;
456.0     40 |
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/EchartsTimeseries.tsx:266:5
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     264 |
456.0     265 |   return (
456.0   > 266 |     <>
456.0         |     ^^
456.0     267 |       <div ref={extraControlRef}>
456.0     268 |         <ExtraControls formData={formData} setControlValue={setControlValue} />
456.0     269 |       </div>
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/EchartsTimeseries.tsx:267:7
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     265 |   return (
456.0     266 |     <>
456.0   > 267 |       <div ref={extraControlRef}>
456.0         |       ^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0     268 |         <ExtraControls formData={formData} setControlValue={setControlValue} />
456.0     269 |       </div>
456.0     270 |       <Echart
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/EchartsTimeseries.tsx:268:9
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     266 |     <>
456.0     267 |       <div ref={extraControlRef}>
456.0   > 268 |         <ExtraControls formData={formData} setControlValue={setControlValue} />
456.0         |         ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0     269 |       </div>
456.0     270 |       <Echart
456.0     271 |         ref={echartRef}
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/EchartsTimeseries.tsx:270:7
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     268 |         <ExtraControls formData={formData} setControlValue={setControlValue} />
456.0     269 |       </div>
456.0   > 270 |       <Echart
456.0         |       ^^^^^^^
456.0   > 271 |         ref={echartRef}
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 272 |         refs={refs}
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 273 |         height={height - extraControlHeight}
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 274 |         width={width}
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 275 |         echartOptions={echartOptions}
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 276 |         eventHandlers={eventHandlers}
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 277 |         zrEventHandlers={zrEventHandlers}
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 278 |         selectedValues={selectedValues}
456.0         | ^^^^^^^^^^^^^^^^^^^^^^^
456.0   > 279 |       />
456.0         | ^^^^^^^^^
456.0     280 |     </>
456.0     281 |   );
456.0     282 | }
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/index.ts:21:26
456.0 TS6142: Module './Regular/Line/controlPanel' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/Timeseries/Regular/Line/controlPanel.tsx', but '--jsx' is not set.
456.0     19 | import { AnnotationType, Behavior, t } from '@superset-ui/core';
456.0     20 | import buildQuery from './buildQuery';
456.0   > 21 | import controlPanel from './Regular/Line/controlPanel';
456.0        |                          ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0     22 | import transformProps from './transformProps';
456.0     23 | import thumbnail from './images/thumbnail.png';
456.0     24 | import {
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/index.ts:39:31
456.0 TS6142: Module './EchartsTimeseries' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/Timeseries/EchartsTimeseries.tsx', but '--jsx' is not set.
456.0     37 |       buildQuery,
456.0     38 |       controlPanel,
456.0   > 39 |       loadChart: () => import('./EchartsTimeseries'),
456.0        |                               ^^^^^^^^^^^^^^^^^^^^^
456.0     40 |       metadata: {
456.0     41 |         behaviors: [
456.0     42 |           Behavior.InteractiveChart,
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Regular/Bar/controlPanel.tsx:42:8
456.0 TS6142: Module '../../../controls' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/controls.tsx', but '--jsx' is not set.
456.0     40 |   xAxisLabelRotation,
456.0     41 |   xAxisLabelInterval,
456.0   > 42 | } from '../../../controls';
456.0        |        ^^^^^^^^^^^^^^^^^^^
456.0     43 |
456.0     44 | import { OrientationType } from '../../types';
456.0     45 | import {
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Regular/Bar/controlPanel.tsx:324:10
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     322 |       expanded: true,
456.0     323 |       controlSetRows: [
456.0   > 324 |         [<ControlSubSectionHeader>{t('X Axis')}</ControlSubSectionHeader>],
456.0         |          ^^^^^^^^^^^^^^^^^^^^^^^^^
456.0     325 |         ...createAxisTitleControl('x'),
456.0     326 |         [<ControlSubSectionHeader>{t('Y Axis')}</ControlSubSectionHeader>],
456.0     327 |         ...createAxisTitleControl('y'),
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Regular/Bar/controlPanel.tsx:326:10
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     324 |         [<ControlSubSectionHeader>{t('X Axis')}</ControlSubSectionHeader>],
456.0     325 |         ...createAxisTitleControl('x'),
456.0   > 326 |         [<ControlSubSectionHeader>{t('Y Axis')}</ControlSubSectionHeader>],
456.0         |          ^^^^^^^^^^^^^^^^^^^^^^^^^
456.0     327 |         ...createAxisTitleControl('y'),
456.0     328 |       ],
456.0     329 |     },
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Regular/Bar/controlPanel.tsx:384:10
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     382 |         ],
456.0     383 |         ...legendSection,
456.0   > 384 |         [<ControlSubSectionHeader>{t('X Axis')}</ControlSubSectionHeader>],
456.0         |          ^^^^^^^^^^^^^^^^^^^^^^^^^
456.0     385 |         ...createAxisControl('x'),
456.0     386 |         [truncateXAxis],
456.0     387 |         [xAxisBounds],
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Regular/Bar/controlPanel.tsx:389:10
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     387 |         [xAxisBounds],
456.0     388 |         ...richTooltipSection,
456.0   > 389 |         [<ControlSubSectionHeader>{t('Y Axis')}</ControlSubSectionHeader>],
456.0         |          ^^^^^^^^^^^^^^^^^^^^^^^^^
456.0     390 |         ...createAxisControl('y'),
456.0     391 |       ],
456.0     392 |     },
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Regular/Bar/index.ts:27:26
456.0 TS6142: Module './controlPanel' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/Timeseries/Regular/Bar/controlPanel.tsx', but '--jsx' is not set.
456.0     25 | import { EchartsChartPlugin } from '../../../types';
456.0     26 | import buildQuery from '../../buildQuery';
456.0   > 27 | import controlPanel from './controlPanel';
456.0        |                          ^^^^^^^^^^^^^^^^
456.0     28 | import transformProps from '../../transformProps';
456.0     29 | import thumbnail from './images/thumbnail.png';
456.0     30 | import example1 from './images/Bar1.png';
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Regular/Bar/index.ts:51:31
456.0 TS6142: Module '../../EchartsTimeseries' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/Timeseries/EchartsTimeseries.tsx', but '--jsx' is not set.
456.0     49 |       buildQuery,
456.0     50 |       controlPanel,
456.0   > 51 |       loadChart: () => import('../../EchartsTimeseries'),
456.0        |                               ^^^^^^^^^^^^^^^^^^^^^^^^^
456.0     52 |       metadata: {
456.0     53 |         behaviors: [
456.0     54 |           Behavior.InteractiveChart,
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Regular/Line/controlPanel.tsx:45:8
456.0 TS6142: Module '../../../controls' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/controls.tsx', but '--jsx' is not set.
456.0     43 |   xAxisLabelRotation,
456.0     44 |   xAxisLabelInterval,
456.0   > 45 | } from '../../../controls';
456.0        |        ^^^^^^^^^^^^^^^^^^^
456.0     46 |
456.0     47 | const {
456.0     48 |   area,
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Regular/Line/controlPanel.tsx:190:10
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     188 |         [minorTicks],
456.0     189 |         ...legendSection,
456.0   > 190 |         [<ControlSubSectionHeader>{t('X Axis')}</ControlSubSectionHeader>],
456.0         |          ^^^^^^^^^^^^^^^^^^^^^^^^^
456.0     191 |         [
456.0     192 |           {
456.0     193 |             name: 'x_axis_time_format',
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Regular/Line/controlPanel.tsx:204:10
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     202 |         [xAxisLabelInterval],
456.0     203 |         ...richTooltipSection,
456.0   > 204 |         [<ControlSubSectionHeader>{t('Y Axis')}</ControlSubSectionHeader>],
456.0         |          ^^^^^^^^^^^^^^^^^^^^^^^^^
456.0     205 |         ['y_axis_format'],
456.0     206 |         ['currency_format'],
456.0     207 |         [
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Regular/Line/index.ts:26:26
456.0 TS6142: Module './controlPanel' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/Timeseries/Regular/Line/controlPanel.tsx', but '--jsx' is not set.
456.0     24 | } from '../../types';
456.0     25 | import buildQuery from '../../buildQuery';
456.0   > 26 | import controlPanel from './controlPanel';
456.0        |                          ^^^^^^^^^^^^^^^^
456.0     27 | import transformProps from '../../transformProps';
456.0     28 | import thumbnail from './images/thumbnail.png';
456.0     29 | import example1 from './images/Line1.png';
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Regular/Line/index.ts:50:31
456.0 TS6142: Module '../../EchartsTimeseries' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/Timeseries/EchartsTimeseries.tsx', but '--jsx' is not set.
456.0     48 |       buildQuery,
456.0     49 |       controlPanel,
456.0   > 50 |       loadChart: () => import('../../EchartsTimeseries'),
456.0        |                               ^^^^^^^^^^^^^^^^^^^^^^^^^
456.0     51 |       metadata: {
456.0     52 |         behaviors: [
456.0     53 |           Behavior.InteractiveChart,
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Regular/Scatter/controlPanel.tsx:44:8
456.0 TS6142: Module '../../../controls' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/controls.tsx', but '--jsx' is not set.
456.0     42 |   xAxisLabelRotation,
456.0     43 |   xAxisLabelInterval,
456.0   > 44 | } from '../../../controls';
456.0        |        ^^^^^^^^^^^^^^^^^^^
456.0     45 |
456.0     46 | const {
456.0     47 |   logAxis,
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Regular/Scatter/controlPanel.tsx:117:10
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     115 |         [minorTicks],
456.0     116 |         ...legendSection,
456.0   > 117 |         [<ControlSubSectionHeader>{t('X Axis')}</ControlSubSectionHeader>],
456.0         |          ^^^^^^^^^^^^^^^^^^^^^^^^^
456.0     118 |
456.0     119 |         [
456.0     120 |           {
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Regular/Scatter/controlPanel.tsx:134:10
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     132 |         ...richTooltipSection,
456.0     133 |         // eslint-disable-next-line react/jsx-key
456.0   > 134 |         [<ControlSubSectionHeader>{t('Y Axis')}</ControlSubSectionHeader>],
456.0         |          ^^^^^^^^^^^^^^^^^^^^^^^^^
456.0     135 |         ['y_axis_format'],
456.0     136 |         ['currency_format'],
456.0     137 |         [
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Regular/Scatter/index.ts:26:26
456.0 TS6142: Module './controlPanel' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/Timeseries/Regular/Scatter/controlPanel.tsx', but '--jsx' is not set.
456.0     24 | } from '../../types';
456.0     25 | import buildQuery from '../../buildQuery';
456.0   > 26 | import controlPanel from './controlPanel';
456.0        |                          ^^^^^^^^^^^^^^^^
456.0     27 | import transformProps from '../../transformProps';
456.0     28 | import thumbnail from './images/thumbnail.png';
456.0     29 | import example1 from './images/Scatter1.png';
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Regular/Scatter/index.ts:49:31
456.0 TS6142: Module '../../EchartsTimeseries' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/Timeseries/EchartsTimeseries.tsx', but '--jsx' is not set.
456.0     47 |       buildQuery,
456.0     48 |       controlPanel,
456.0   > 49 |       loadChart: () => import('../../EchartsTimeseries'),
456.0        |                               ^^^^^^^^^^^^^^^^^^^^^^^^^
456.0     50 |       metadata: {
456.0     51 |         behaviors: [
456.0     52 |           Behavior.InteractiveChart,
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Regular/SmoothLine/controlPanel.tsx:44:8
456.0 TS6142: Module '../../../controls' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/controls.tsx', but '--jsx' is not set.
456.0     42 |   xAxisLabelRotation,
456.0     43 |   xAxisLabelInterval,
456.0   > 44 | } from '../../../controls';
456.0        |        ^^^^^^^^^^^^^^^^^^^
456.0     45 |
456.0     46 | const {
456.0     47 |   logAxis,
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Regular/SmoothLine/controlPanel.tsx:117:10
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     115 |         [minorTicks],
456.0     116 |         ...legendSection,
456.0   > 117 |         [<ControlSubSectionHeader>{t('X Axis')}</ControlSubSectionHeader>],
456.0         |          ^^^^^^^^^^^^^^^^^^^^^^^^^
456.0     118 |         [
456.0     119 |           {
456.0     120 |             name: 'x_axis_time_format',
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Regular/SmoothLine/controlPanel.tsx:133:10
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     131 |         ...richTooltipSection,
456.0     132 |         // eslint-disable-next-line react/jsx-key
456.0   > 133 |         [<ControlSubSectionHeader>{t('Y Axis')}</ControlSubSectionHeader>],
456.0         |          ^^^^^^^^^^^^^^^^^^^^^^^^^
456.0     134 |
456.0     135 |         ['y_axis_format'],
456.0     136 |         ['currency_format'],
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Regular/SmoothLine/index.ts:26:26
456.0 TS6142: Module './controlPanel' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/Timeseries/Regular/SmoothLine/controlPanel.tsx', but '--jsx' is not set.
456.0     24 | } from '../../types';
456.0     25 | import buildQuery from '../../buildQuery';
456.0   > 26 | import controlPanel from './controlPanel';
456.0        |                          ^^^^^^^^^^^^^^^^
456.0     27 | import transformProps from '../../transformProps';
456.0     28 | import thumbnail from './images/thumbnail.png';
456.0     29 | import example1 from './images/SmoothLine1.png';
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Regular/SmoothLine/index.ts:49:31
456.0 TS6142: Module '../../EchartsTimeseries' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/Timeseries/EchartsTimeseries.tsx', but '--jsx' is not set.
456.0     47 |       buildQuery,
456.0     48 |       controlPanel,
456.0   > 49 |       loadChart: () => import('../../EchartsTimeseries'),
456.0        |                               ^^^^^^^^^^^^^^^^^^^^^^^^^
456.0     50 |       metadata: {
456.0     51 |         behaviors: [
456.0     52 |           Behavior.InteractiveChart,
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Step/controlPanel.tsx:42:8
456.0 TS6142: Module '../../controls' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/controls.tsx', but '--jsx' is not set.
456.0     40 |   xAxisLabelRotation,
456.0     41 |   xAxisLabelInterval,
456.0   > 42 | } from '../../controls';
456.0        |        ^^^^^^^^^^^^^^^^
456.0     43 |
456.0     44 | const {
456.0     45 |   area,
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Step/controlPanel.tsx:169:10
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     167 |         [minorTicks],
456.0     168 |         ...legendSection,
456.0   > 169 |         [<ControlSubSectionHeader>{t('X Axis')}</ControlSubSectionHeader>],
456.0         |          ^^^^^^^^^^^^^^^^^^^^^^^^^
456.0     170 |         [
456.0     171 |           {
456.0     172 |             name: 'x_axis_time_format',
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Step/controlPanel.tsx:184:10
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     182 |         ...richTooltipSection,
456.0     183 |         // eslint-disable-next-line react/jsx-key
456.0   > 184 |         [<ControlSubSectionHeader>{t('Y Axis')}</ControlSubSectionHeader>],
456.0         |          ^^^^^^^^^^^^^^^^^^^^^^^^^
456.0     185 |         ['y_axis_format'],
456.0     186 |         ['currency_format'],
456.0     187 |         [
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Step/index.ts:22:26
456.0 TS6142: Module './controlPanel' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/Timeseries/Step/controlPanel.tsx', but '--jsx' is not set.
456.0     20 | import { EchartsTimeseriesChartProps, EchartsTimeseriesFormData } from '../..';
456.0     21 | import buildQuery from '../buildQuery';
456.0   > 22 | import controlPanel from './controlPanel';
456.0        |                          ^^^^^^^^^^^^^^^^
456.0     23 | import transformProps from '../transformProps';
456.0     24 | import thumbnail from './images/thumbnail.png';
456.0     25 | import example1 from './images/Step1.png';
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Step/index.ts:37:31
456.0 TS6142: Module '../EchartsTimeseries' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/Timeseries/EchartsTimeseries.tsx', but '--jsx' is not set.
456.0     35 |       buildQuery,
456.0     36 |       controlPanel,
456.0   > 37 |       loadChart: () => import('../EchartsTimeseries'),
456.0        |                               ^^^^^^^^^^^^^^^^^^^^^^
456.0     38 |       metadata: {
456.0     39 |         behaviors: [
456.0     40 |           Behavior.InteractiveChart,
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformers.ts:28:3
456.0 TS2724: '"@superset-ui/core"' has no exported member named 'isTimeseriesAnnotationResult'. Did you mean 'isTimeseriesAnnotationLayer'?
456.0     26 |   FormulaAnnotationLayer,
456.0     27 |   IntervalAnnotationLayer,
456.0   > 28 |   isTimeseriesAnnotationResult,
456.0        |   ^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0     29 |   LegendState,
456.0     30 |   SupersetTheme,
456.0     31 |   TimeseriesAnnotationLayer,
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformers.ts:428:24
456.0 TS2339: Property 'colors' does not exist on type 'SupersetTheme'.
456.0     426 |       ? {
456.0     427 |           show: true,
456.0   > 428 |           color: theme.colors.grayscale.dark2,
456.0         |                        ^^^^^^
456.0     429 |           position: 'insideTop',
456.0     430 |           verticalAlign: 'top',
456.0     431 |           fontWeight: 'bold',
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformers.ts:436:36
456.0 TS2339: Property 'colors' does not exist on type 'SupersetTheme'.
456.0     434 |             position: 'insideTop',
456.0     435 |             verticalAlign: 'top',
456.0   > 436 |             backgroundColor: theme.colors.grayscale.light5,
456.0         |                                    ^^^^^^
456.0     437 |           },
456.0     438 |         }
456.0     439 |       : {
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformers.ts:441:24
456.0 TS2339: Property 'colors' does not exist on type 'SupersetTheme'.
456.0     439 |       : {
456.0     440 |           show: false,
456.0   > 441 |           color: theme.colors.grayscale.dark2,
456.0         |                        ^^^^^^
456.0     442 |           // @ts-ignore
456.0     443 |           emphasis: {
456.0     444 |             fontWeight: 'bold',
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformers.ts:448:36
456.0 TS2339: Property 'colors' does not exist on type 'SupersetTheme'.
456.0     446 |             position: 'insideTop',
456.0     447 |             verticalAlign: 'top',
456.0   > 448 |             backgroundColor: theme.colors.grayscale.light5,
456.0         |                                    ^^^^^^
456.0     449 |           },
456.0     450 |         };
456.0     451 |     series.push({
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformers.ts:509:24
456.0 TS2339: Property 'colors' does not exist on type 'SupersetTheme'.
456.0     507 |       ? {
456.0     508 |           show: true,
456.0   > 509 |           color: theme.colors.grayscale.dark2,
456.0         |                        ^^^^^^
456.0     510 |           position: 'insideEndTop',
456.0     511 |           fontWeight: 'bold',
456.0     512 |           formatter: (params: CallbackDataParams) => params.name,
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformers.ts:515:36
456.0 TS2339: Property 'colors' does not exist on type 'SupersetTheme'.
456.0     513 |           // @ts-ignore
456.0     514 |           emphasis: {
456.0   > 515 |             backgroundColor: theme.colors.grayscale.light5,
456.0         |                                    ^^^^^^
456.0     516 |           },
456.0     517 |         }
456.0     518 |       : {
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformers.ts:520:24
456.0 TS2339: Property 'colors' does not exist on type 'SupersetTheme'.
456.0     518 |       : {
456.0     519 |           show: false,
456.0   > 520 |           color: theme.colors.grayscale.dark2,
456.0         |                        ^^^^^^
456.0     521 |           position: 'insideEndTop',
456.0     522 |           // @ts-ignore
456.0     523 |           emphasis: {
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformers.ts:527:36
456.0 TS2339: Property 'colors' does not exist on type 'SupersetTheme'.
456.0     525 |             fontWeight: 'bold',
456.0     526 |             show: true,
456.0   > 527 |             backgroundColor: theme.colors.grayscale.light5,
456.0         |                                    ^^^^^^
456.0     528 |           },
456.0     529 |         };
456.0     530 |
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformers.ts:561:12
456.0 TS2339: Property 'forEach' does not exist on type 'AnnotationResult'.
456.0     559 |   const isHorizontal = orientation === OrientationType.Horizontal;
456.0     560 |   if (isTimeseriesAnnotationResult(result)) {
456.0   > 561 |     result.forEach(annotation => {
456.0         |            ^^^^^^^
456.0     562 |       const { key, values } = annotation;
456.0     563 |       series.push({
456.0     564 |         type: 'line',
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:29:3
456.0 TS2305: Module '"@superset-ui/core"' has no exported member 'GenericDataType'.
456.0     27 |   ensureIsArray,
456.0     28 |   tooltipHtml,
456.0   > 29 |   GenericDataType,
456.0        |   ^^^^^^^^^^^^^^^
456.0     30 |   getCustomFormatter,
456.0     31 |   getMetricLabel,
456.0     32 |   getNumberFormatter,
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Tree/controlPanel.tsx:107:10
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     105 |       expanded: true,
456.0     106 |       controlSetRows: [
456.0   > 107 |         [<ControlSubSectionHeader>{t('Layout')}</ControlSubSectionHeader>],
456.0         |          ^^^^^^^^^^^^^^^^^^^^^^^^^
456.0     108 |         [
456.0     109 |           {
456.0     110 |             name: 'layout',
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Tree/EchartsTree.tsx:20:20
456.0 TS6142: Module '../components/Echart' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/components/Echart.tsx', but '--jsx' is not set.
456.0     18 |  */
456.0     19 | import { EchartsProps } from '../types';
456.0   > 20 | import Echart from '../components/Echart';
456.0        |                    ^^^^^^^^^^^^^^^^^^^^^^
456.0     21 |
456.0     22 | export default function EchartsGraph({
456.0     23 |   echartOptions,
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Tree/EchartsTree.tsx:29:5
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     27 | }: EchartsProps) {
456.0     28 |   return (
456.0   > 29 |     <Echart
456.0        |     ^^^^^^^
456.0   > 30 |       refs={refs}
456.0        | ^^^^^^^^^^^^^^^^^
456.0   > 31 |       height={height}
456.0        | ^^^^^^^^^^^^^^^^^
456.0   > 32 |       width={width}
456.0        | ^^^^^^^^^^^^^^^^^
456.0   > 33 |       echartOptions={echartOptions}
456.0        | ^^^^^^^^^^^^^^^^^
456.0   > 34 |     />
456.0        | ^^^^^^^
456.0     35 |   );
456.0     36 | }
456.0     37 |
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Tree/index.ts:20:26
456.0 TS6142: Module './controlPanel' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/Tree/controlPanel.tsx', but '--jsx' is not set.
456.0     18 |  */
456.0     19 | import { t } from '@superset-ui/core';
456.0   > 20 | import controlPanel from './controlPanel';
456.0        |                          ^^^^^^^^^^^^^^^^
456.0     21 | import transformProps from './transformProps';
456.0     22 | import thumbnail from './images/thumbnail.png';
456.0     23 | import example from './images/tree.png';
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Tree/index.ts:32:31
456.0 TS6142: Module './EchartsTree' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/Tree/EchartsTree.tsx', but '--jsx' is not set.
456.0     30 |       buildQuery,
456.0     31 |       controlPanel,
456.0   > 32 |       loadChart: () => import('./EchartsTree'),
456.0        |                               ^^^^^^^^^^^^^^^
456.0     33 |       metadata: {
456.0     34 |         category: t('Part of a Whole'),
456.0     35 |         credits: ['https://echarts.apache.org'],
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Treemap/controlPanel.tsx:52:10
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     50 |       controlSetRows: [
456.0     51 |         ['color_scheme'],
456.0   > 52 |         [<ControlSubSectionHeader>{t('Labels')}</ControlSubSectionHeader>],
456.0        |          ^^^^^^^^^^^^^^^^^^^^^^^^^
456.0     53 |         [
456.0     54 |           {
456.0     55 |             name: 'show_labels',
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Treemap/EchartsTreemap.tsx:27:20
456.0 TS6142: Module '../components/Echart' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/components/Echart.tsx', but '--jsx' is not set.
456.0     25 | } from '@superset-ui/core';
456.0     26 | import { useCallback } from 'react';
456.0   > 27 | import Echart from '../components/Echart';
456.0        |                    ^^^^^^^^^^^^^^^^^^^^^^
456.0     28 | import { NULL_STRING } from '../constants';
456.0     29 | import { EventHandlers } from '../types';
456.0     30 | import { extractTreePathInfo } from './constants';
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Treemap/EchartsTreemap.tsx:159:5
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     157 |
456.0     158 |   return (
456.0   > 159 |     <Echart
456.0         |     ^^^^^^^
456.0   > 160 |       refs={refs}
456.0         | ^^^^^^^^^^^^^^^^^
456.0   > 161 |       height={height}
456.0         | ^^^^^^^^^^^^^^^^^
456.0   > 162 |       width={width}
456.0         | ^^^^^^^^^^^^^^^^^
456.0   > 163 |       echartOptions={echartOptions}
456.0         | ^^^^^^^^^^^^^^^^^
456.0   > 164 |       eventHandlers={eventHandlers}
456.0         | ^^^^^^^^^^^^^^^^^
456.0   > 165 |       selectedValues={selectedValues}
456.0         | ^^^^^^^^^^^^^^^^^
456.0   > 166 |     />
456.0         | ^^^^^^^
456.0     167 |   );
456.0     168 | }
456.0     169 |
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Treemap/index.ts:22:26
456.0 TS6142: Module './controlPanel' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/Treemap/controlPanel.tsx', but '--jsx' is not set.
456.0     20 | import { Behavior, t } from '@superset-ui/core';
456.0     21 | import buildQuery from './buildQuery';
456.0   > 22 | import controlPanel from './controlPanel';
456.0        |                          ^^^^^^^^^^^^^^^^
456.0     23 | import transformProps from './transformProps';
456.0     24 | import thumbnail from './images/thumbnail.png';
456.0     25 | import example1 from './images/treemap_v2_1.png';
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Treemap/index.ts:48:31
456.0 TS6142: Module './EchartsTreemap' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/Treemap/EchartsTreemap.tsx', but '--jsx' is not set.
456.0     46 |       buildQuery,
456.0     47 |       controlPanel,
456.0   > 48 |       loadChart: () => import('./EchartsTreemap'),
456.0        |                               ^^^^^^^^^^^^^^^^^^
456.0     49 |       metadata: {
456.0     50 |         behaviors: [
456.0     51 |           Behavior.InteractiveChart,
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Treemap/transformProps.ts:242:22
456.0 TS2339: Property 'colors' does not exist on type 'SupersetTheme'.
456.0     240 |       },
456.0     241 |       itemStyle: {
456.0   > 242 |         color: theme.colors.primary.base,
456.0         |                      ^^^^^^
456.0     243 |       },
456.0     244 |     },
456.0     245 |   ];
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Treemap/transformProps.ts:268:22
456.0 TS2339: Property 'colors' does not exist on type 'SupersetTheme'.
456.0     266 |         position: labelPosition,
456.0     267 |         formatter,
456.0   > 268 |         color: theme.colors.grayscale.dark2,
456.0         |                      ^^^^^^
456.0     269 |         fontSize: treemapFont||LABEL_FONTSIZE,
456.0     270 |       },
456.0     271 |       upperLabel: {
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/utils/annotation.ts:32:3
456.0 TS2724: '"@superset-ui/core"' has no exported member named 'isRecordAnnotationResult'. Did you mean 'AnnotationResult'?
456.0     30 |   evalExpression,
456.0     31 |   FormulaAnnotationLayer,
456.0   > 32 |   isRecordAnnotationResult,
456.0        |   ^^^^^^^^^^^^^^^^^^^^^^^^
456.0     33 |   isTableAnnotationLayer,
456.0     34 |   isTimeseriesAnnotationResult,
456.0     35 | } from '@superset-ui/core';
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/utils/annotation.ts:34:3
456.0 TS2724: '"@superset-ui/core"' has no exported member named 'isTimeseriesAnnotationResult'. Did you mean 'isTimeseriesAnnotationLayer'?
456.0     32 |   isRecordAnnotationResult,
456.0     33 |   isTableAnnotationLayer,
456.0   > 34 |   isTimeseriesAnnotationResult,
456.0        |   ^^^^^^^^^^^^^^^^^^^^^^^^^^^^
456.0     35 | } from '@superset-ui/core';
456.0     36 | import { EchartsTimeseriesChartProps } from '../types';
456.0     37 | import { EchartsMixedTimeseriesProps } from '../MixedTimeseries/types';
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/utils/annotation.ts:137:18
456.0 TS2339: Property 'map' does not exist on type 'AnnotationResult'.
456.0     135 |       const result = data[anno.name];
456.0     136 |       return isTimeseriesAnnotationResult(result)
456.0   > 137 |         ? result.map(annoSeries => annoSeries.key)
456.0         |                  ^^^
456.0     138 |         : [];
456.0     139 |     });
456.0     140 |
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:27:3
456.0 TS2305: Module '"@superset-ui/core"' has no exported member 'GenericDataType'.
456.0     25 |   DTTM_ALIAS,
456.0     26 |   ensureIsArray,
456.0   > 27 |   GenericDataType,
456.0        |   ^^^^^^^^^^^^^^^
456.0     28 |   LegendState,
456.0     29 |   normalizeTimestamp,
456.0     30 |   NumberFormats,
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/controlPanel.tsx:28:34
456.0 TS6142: Module '../controls' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/controls.tsx', but '--jsx' is not set.
456.0     26 |   sharedControls,
456.0     27 | } from '@superset-ui/chart-controls';
456.0   > 28 | import { showValueControl } from '../controls';
456.0        |                                  ^^^^^^^^^^^^^
456.0     29 |
456.0     30 | const config: ControlPanelConfig = {
456.0     31 |   controlPanelSections: [
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/controlPanel.tsx:75:11
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     73 |
456.0     74 |         [
456.0   > 75 |           <ControlSubSectionHeader>
456.0        |           ^^^^^^^^^^^^^^^^^^^^^^^^^
456.0     76 |             {t('Series colors')}
456.0     77 |           </ControlSubSectionHeader>,
456.0     78 |         ],
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/controlPanel.tsx:108:10
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     106 |           },
456.0     107 |         ],
456.0   > 108 |         [<ControlSubSectionHeader>{t('X Axis')}</ControlSubSectionHeader>],
456.0         |          ^^^^^^^^^^^^^^^^^^^^^^^^^
456.0     109 |         [
456.0     110 |           {
456.0     111 |             name: 'x_axis_label',
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/controlPanel.tsx:150:10
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     148 |           },
456.0     149 |         ],
456.0   > 150 |         [<ControlSubSectionHeader>{t('Y Axis')}</ControlSubSectionHeader>],
456.0         |          ^^^^^^^^^^^^^^^^^^^^^^^^^
456.0     151 |         [
456.0     152 |           {
456.0     153 |             name: 'y_axis_label',
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/EchartsWaterfall.tsx:19:20
456.0 TS6142: Module '../components/Echart' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/components/Echart.tsx', but '--jsx' is not set.
456.0     17 |  * under the License.
456.0     18 |  */
456.0   > 19 | import Echart from '../components/Echart';
456.0        |                    ^^^^^^^^^^^^^^^^^^^^^^
456.0     20 | import { WaterfallChartTransformedProps } from './types';
456.0     21 | import { EventHandlers } from '../types';
456.0     22 |
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/EchartsWaterfall.tsx:41:5
456.0 TS17004: Cannot use JSX unless the '--jsx' flag is provided.
456.0     39 |
456.0     40 |   return (
456.0   > 41 |     <Echart
456.0        |     ^^^^^^^
456.0   > 42 |       refs={refs}
456.0        | ^^^^^^^^^^^^^^^^^
456.0   > 43 |       height={height}
456.0        | ^^^^^^^^^^^^^^^^^
456.0   > 44 |       width={width}
456.0        | ^^^^^^^^^^^^^^^^^
456.0   > 45 |       echartOptions={echartOptions}
456.0        | ^^^^^^^^^^^^^^^^^
456.0   > 46 |       eventHandlers={eventHandlers}
456.0        | ^^^^^^^^^^^^^^^^^
456.0   > 47 |     />
456.0        | ^^^^^^^
456.0     48 |   );
456.0     49 | }
456.0     50 |
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/index.ts:22:26
456.0 TS6142: Module './controlPanel' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/Waterfall/controlPanel.tsx', but '--jsx' is not set.
456.0     20 | import { ChartMetadata, ChartPlugin, t } from '@superset-ui/core';
456.0     21 | import buildQuery from './buildQuery';
456.0   > 22 | import controlPanel from './controlPanel';
456.0        |                          ^^^^^^^^^^^^^^^^
456.0     23 | import transformProps from './transformProps';
456.0     24 | import thumbnail from './images/thumbnail.png';
456.0     25 | import example1 from './images/example1.png';
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/index.ts:49:31
456.0 TS6142: Module './EchartsWaterfall' was resolved to '/app/superset-frontend/plugins/plugin-chart-echarts/src/Waterfall/EchartsWaterfall.tsx', but '--jsx' is not set.
456.0     47 |       buildQuery,
456.0     48 |       controlPanel,
456.0   > 49 |       loadChart: () => import('./EchartsWaterfall'),
456.0        |                               ^^^^^^^^^^^^^^^^^^^^
456.0     50 |       metadata: new ChartMetadata({
456.0     51 |         credits: ['https://echarts.apache.org'],
456.0     52 |         category: t('Evolution'),
456.0
456.0 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/transformProps.ts:23:3
456.0 TS2305: Module '"@superset-ui/core"' has no exported member 'GenericDataType'.
456.0     21 |   DataRecord,
456.0     22 |   ensureIsArray,
456.0   > 23 |   GenericDataType,
456.0        |   ^^^^^^^^^^^^^^^
456.0     24 |   getMetricLabel,
456.0     25 |   getNumberFormatter,
456.0     26 |   getTimeFormatter,
456.0
456.0 webpack 5.99.9 compiled with 226 errors and 24 warnings in 434566 ms
------
target superset-worker: failed to solve: process "/bin/sh -c if [ \"${DEV_MODE}\" = \"false\" ]; then       echo \"Running 'npm run ${BUILD_CMD}'\";       npm run ${BUILD_CMD};     else       echo \"Skipping 'npm run ${BUILD_CMD}' in dev mode\";     fi" did not complete successfully: exit code: 1

root@EC03-INS-LHUB01:/home/CORP/re_priyanshug1/ss/superset#
