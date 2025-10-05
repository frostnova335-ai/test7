235.3 TS2304: Cannot find name 'getNumberFormatter'.
235.3     281 |           currency: currencyFormat,
235.3     282 |         })
235.3   > 283 |       : getNumberFormatter(yAxisFormat);
235.3         |         ^^^^^^^^^^^^^^^^^^
235.3     284 |   const formatterSecondary = contributionMode
235.3     285 |     ? getNumberFormatter(',.0%')
235.3     286 |     : currencyFormatSecondary?.symbol
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/MixedTimeseries/transformProps.ts:285:7
235.3 TS2304: Cannot find name 'getNumberFormatter'.
235.3     283 |       : getNumberFormatter(yAxisFormat);
235.3     284 |   const formatterSecondary = contributionMode
235.3   > 285 |     ? getNumberFormatter(',.0%')
235.3         |       ^^^^^^^^^^^^^^^^^^
235.3     286 |     : currencyFormatSecondary?.symbol
235.3     287 |       ? new CurrencyFormatter({
235.3     288 |           d3Format: yAxisFormatSecondary,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/MixedTimeseries/transformProps.ts:287:13
235.3 TS2304: Cannot find name 'CurrencyFormatter'.
235.3     285 |     ? getNumberFormatter(',.0%')
235.3     286 |     : currencyFormatSecondary?.symbol
235.3   > 287 |       ? new CurrencyFormatter({
235.3         |             ^^^^^^^^^^^^^^^^^
235.3     288 |           d3Format: yAxisFormatSecondary,
235.3     289 |           currency: currencyFormatSecondary,
235.3     290 |         })
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/MixedTimeseries/transformProps.ts:291:9
235.3 TS2304: Cannot find name 'getNumberFormatter'.
235.3     289 |           currency: currencyFormatSecondary,
235.3     290 |         })
235.3   > 291 |       : getNumberFormatter(yAxisFormatSecondary);
235.3         |         ^^^^^^^^^^^^^^^^^^
235.3     292 |   const customFormatters = buildCustomFormatters(
235.3     293 |     [...ensureIsArray(metrics), ...ensureIsArray(metricsB)],
235.3     294 |     currencyFormats,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/MixedTimeseries/transformProps.ts:292:28
235.3 TS2304: Cannot find name 'buildCustomFormatters'.
235.3     290 |         })
235.3     291 |       : getNumberFormatter(yAxisFormatSecondary);
235.3   > 292 |   const customFormatters = buildCustomFormatters(
235.3         |                            ^^^^^^^^^^^^^^^^^^^^^
235.3     293 |     [...ensureIsArray(metrics), ...ensureIsArray(metricsB)],
235.3     294 |     currencyFormats,
235.3     295 |     columnFormats,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/MixedTimeseries/transformProps.ts:293:9
235.3 TS2304: Cannot find name 'ensureIsArray'.
235.3     291 |       : getNumberFormatter(yAxisFormatSecondary);
235.3     292 |   const customFormatters = buildCustomFormatters(
235.3   > 293 |     [...ensureIsArray(metrics), ...ensureIsArray(metricsB)],
235.3         |         ^^^^^^^^^^^^^
235.3     294 |     currencyFormats,
235.3     295 |     columnFormats,
235.3     296 |     yAxisFormat,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/MixedTimeseries/transformProps.ts:293:36
235.3 TS2304: Cannot find name 'ensureIsArray'.
235.3     291 |       : getNumberFormatter(yAxisFormatSecondary);
235.3     292 |   const customFormatters = buildCustomFormatters(
235.3   > 293 |     [...ensureIsArray(metrics), ...ensureIsArray(metricsB)],
235.3         |                                    ^^^^^^^^^^^^^
235.3     294 |     currencyFormats,
235.3     295 |     columnFormats,
235.3     296 |     yAxisFormat,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/MixedTimeseries/transformProps.ts:299:37
235.3 TS2304: Cannot find name 'buildCustomFormatters'.
235.3     297 |     currencyFormat,
235.3     298 |   );
235.3   > 299 |   const customFormattersSecondary = buildCustomFormatters(
235.3         |                                     ^^^^^^^^^^^^^^^^^^^^^
235.3     300 |     [...ensureIsArray(metrics), ...ensureIsArray(metricsB)],
235.3     301 |     currencyFormats,
235.3     302 |     columnFormats,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/MixedTimeseries/transformProps.ts:300:9
235.3 TS2304: Cannot find name 'ensureIsArray'.
235.3     298 |   );
235.3     299 |   const customFormattersSecondary = buildCustomFormatters(
235.3   > 300 |     [...ensureIsArray(metrics), ...ensureIsArray(metricsB)],
235.3         |         ^^^^^^^^^^^^^
235.3     301 |     currencyFormats,
235.3     302 |     columnFormats,
235.3     303 |     yAxisFormatSecondary,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/MixedTimeseries/transformProps.ts:300:36
235.3 TS2304: Cannot find name 'ensureIsArray'.
235.3     298 |   );
235.3     299 |   const customFormattersSecondary = buildCustomFormatters(
235.3   > 300 |     [...ensureIsArray(metrics), ...ensureIsArray(metricsB)],
235.3         |                                    ^^^^^^^^^^^^^
235.3     301 |     currencyFormats,
235.3     302 |     columnFormats,
235.3     303 |     yAxisFormatSecondary,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/MixedTimeseries/transformProps.ts:335:21
235.3 TS2304: Cannot find name 'AnnotationLayer'.
235.3     333 |
235.3     334 |   annotationLayers
235.3   > 335 |     .filter((layer: AnnotationLayer) => layer.show)
235.3         |                     ^^^^^^^^^^^^^^^
235.3     336 |     .forEach((layer: AnnotationLayer) => {
235.3     337 |       if (isFormulaAnnotationLayer(layer))
235.3     338 |         series.push(
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/MixedTimeseries/transformProps.ts:336:22
235.3 TS2304: Cannot find name 'AnnotationLayer'.
235.3     334 |   annotationLayers
235.3     335 |     .filter((layer: AnnotationLayer) => layer.show)
235.3   > 336 |     .forEach((layer: AnnotationLayer) => {
235.3         |                      ^^^^^^^^^^^^^^^
235.3     337 |       if (isFormulaAnnotationLayer(layer))
235.3     338 |         series.push(
235.3     339 |           transformFormulaAnnotation(
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/MixedTimeseries/transformProps.ts:337:11
235.3 TS2304: Cannot find name 'isFormulaAnnotationLayer'.
235.3     335 |     .filter((layer: AnnotationLayer) => layer.show)
235.3     336 |     .forEach((layer: AnnotationLayer) => {
235.3   > 337 |       if (isFormulaAnnotationLayer(layer))
235.3         |           ^^^^^^^^^^^^^^^^^^^^^^^^
235.3     338 |         series.push(
235.3     339 |           transformFormulaAnnotation(
235.3     340 |             layer,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/MixedTimeseries/transformProps.ts:348:16
235.3 TS2304: Cannot find name 'isIntervalAnnotationLayer'.
235.3     346 |           ),
235.3     347 |         );
235.3   > 348 |       else if (isIntervalAnnotationLayer(layer)) {
235.3         |                ^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     349 |         series.push(
235.3     350 |           ...transformIntervalAnnotation(
235.3     351 |             layer,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/MixedTimeseries/transformProps.ts:359:18
235.3 TS2304: Cannot find name 'isEventAnnotationLayer'.
235.3     357 |           ),
235.3     358 |         );
235.3   > 359 |       } else if (isEventAnnotationLayer(layer)) {
235.3         |                  ^^^^^^^^^^^^^^^^^^^^^^
235.3     360 |         series.push(
235.3     361 |           ...transformEventAnnotation(
235.3     362 |             layer,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/MixedTimeseries/transformProps.ts:370:18
235.3 TS2304: Cannot find name 'isTimeseriesAnnotationLayer'.
235.3     368 |           ),
235.3     369 |         );
235.3   > 370 |       } else if (isTimeseriesAnnotationLayer(layer)) {
235.3         |                  ^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     371 |         series.push(
235.3     372 |           ...transformTimeseriesAnnotation(
235.3     373 |             layer,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/MixedTimeseries/transformProps.ts:391:17
235.3 TS2304: Cannot find name 'ensureIsArray'.
235.3     389 |   );
235.3     390 |
235.3   > 391 |   const array = ensureIsArray(chartProps.rawFormData?.time_compare);
235.3         |                 ^^^^^^^^^^^^^
235.3     392 |   const inverted = invert(verboseMap);
235.3     393 |
235.3     394 |   rawSeriesA.forEach(entry => {
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/MixedTimeseries/transformProps.ts:519:23
235.3 TS2304: Cannot find name 'GenericDataType'.
235.3     517 |
235.3     518 |   const tooltipFormatter =
235.3   > 519 |     xAxisDataType === GenericDataType.Temporal
235.3         |                       ^^^^^^^^^^^^^^^
235.3     520 |       ? getTooltipTimeFormatter(tooltipTimeFormat)
235.3     521 |       : String;
235.3     522 |   const xAxisFormatter =
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/MixedTimeseries/transformProps.ts:523:23
235.3 TS2304: Cannot find name 'GenericDataType'.
235.3     521 |       : String;
235.3     522 |   const xAxisFormatter =
235.3   > 523 |     xAxisDataType === GenericDataType.Temporal
235.3         |                       ^^^^^^^^^^^^^^^
235.3     524 |       ? getXAxisFormatter(xAxisTimeFormat)
235.3     525 |       : String;
235.3     526 |
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/MixedTimeseries/transformProps.ts:563:23
235.3 TS2304: Cannot find name 'AxisType'.
235.3     561 |       minorTick: { show: minorTicks },
235.3     562 |       minInterval:
235.3   > 563 |         xAxisType === AxisType.Time && timeGrainSqla
235.3         |                       ^^^^^^^^
235.3     564 |           ? TIMEGRAIN_TO_TIMESTAMP[
235.3     565 |               timeGrainSqla as keyof typeof TIMEGRAIN_TO_TIMESTAMP
235.3     566 |             ]
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/MixedTimeseries/transformProps.ts:688:16
235.3 TS2304: Cannot find name 'tooltipHtml'.
235.3     686 |             }
235.3     687 |           });
235.3   > 688 |         return tooltipHtml(rows, tooltipFormatter(xValue), focusedRow);
235.3         |                ^^^^^^^^^^^
235.3     689 |       },
235.3     690 |     },
235.3     691 |     legend: {
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/MixedTimeseries/types.ts:20:8
235.3 TS1141: String literal expected.
235.3     18 |  */
235.3     19 | import {
235.3   > 20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3        |        ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     21 |   AnnotationLayer,
235.3     22 |   TimeGranularity,
235.3     23 |   QueryFormData,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/MixedTimeseries/types.ts:20:118
235.3 TS2304: Cannot find name 'from'.
235.3     18 |  */
235.3     19 | import {
235.3   > 20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3        |                                                                                                                      ^^^^
235.3     21 |   AnnotationLayer,
235.3     22 |   TimeGranularity,
235.3     23 |   QueryFormData,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/MixedTimeseries/types.ts:21:3
235.3 TS2304: Cannot find name 'AnnotationLayer'.
235.3     19 | import {
235.3     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 21 |   AnnotationLayer,
235.3        |   ^^^^^^^^^^^^^^^
235.3     22 |   TimeGranularity,
235.3     23 |   QueryFormData,
235.3     24 |   QueryFormColumn,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/MixedTimeseries/types.ts:21:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     19 | import {
235.3     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 21 |   AnnotationLayer,
235.3        |   ^^^^^^^^^^^^^^^
235.3     22 |   TimeGranularity,
235.3     23 |   QueryFormData,
235.3     24 |   QueryFormColumn,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/MixedTimeseries/types.ts:21:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     19 | import {
235.3     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 21 |   AnnotationLayer,
235.3        |   ^^^^^^^^^^^^^^^^
235.3   > 22 |   TimeGranularity,
235.3        | ^^^^^^^^^^^^^^^^^^
235.3     23 |   QueryFormData,
235.3     24 |   QueryFormColumn,
235.3     25 |   ContributionType,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/MixedTimeseries/types.ts:21:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     19 | import {
235.3     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 21 |   AnnotationLayer,
235.3        |   ^^^^^^^^^^^^^^^^
235.3   > 22 |   TimeGranularity,
235.3        | ^^^^^^^^^^^^^^^^^^
235.3   > 23 |   QueryFormData,
235.3        | ^^^^^^^^^^^^^^^^
235.3     24 |   QueryFormColumn,
235.3     25 |   ContributionType,
235.3     26 |   TimeFormatter,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/MixedTimeseries/types.ts:21:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     19 | import {
235.3     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 21 |   AnnotationLayer,
235.3        |   ^^^^^^^^^^^^^^^^
235.3   > 22 |   TimeGranularity,
235.3        | ^^^^^^^^^^^^^^^^^^
235.3   > 23 |   QueryFormData,
235.3        | ^^^^^^^^^^^^^^^^^^
235.3   > 24 |   QueryFormColumn,
235.3        | ^^^^^^^^^^^^^^^^^^
235.3     25 |   ContributionType,
235.3     26 |   TimeFormatter,
235.3     27 |   AxisType,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/MixedTimeseries/types.ts:21:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     19 | import {
235.3     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 21 |   AnnotationLayer,
235.3        |   ^^^^^^^^^^^^^^^^
235.3   > 22 |   TimeGranularity,
235.3        | ^^^^^^^^^^^^^^^^^^
235.3   > 23 |   QueryFormData,
235.3        | ^^^^^^^^^^^^^^^^^^
235.3   > 24 |   QueryFormColumn,
235.3        | ^^^^^^^^^^^^^^^^^^
235.3   > 25 |   ContributionType,
235.3        | ^^^^^^^^^^^^^^^^^^^
235.3     26 |   TimeFormatter,
235.3     27 |   AxisType,
235.3     28 | } from '@superset-ui/core';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/MixedTimeseries/types.ts:21:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     19 | import {
235.3     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 21 |   AnnotationLayer,
235.3        |   ^^^^^^^^^^^^^^^^
235.3   > 22 |   TimeGranularity,
235.3        | ^^^^^^^^^^^^^^^^^^
235.3   > 23 |   QueryFormData,
235.3        | ^^^^^^^^^^^^^^^^^^
235.3   > 24 |   QueryFormColumn,
235.3        | ^^^^^^^^^^^^^^^^^^
235.3   > 25 |   ContributionType,
235.3        | ^^^^^^^^^^^^^^^^^^
235.3   > 26 |   TimeFormatter,
235.3        | ^^^^^^^^^^^^^^^^
235.3     27 |   AxisType,
235.3     28 | } from '@superset-ui/core';
235.3     29 | import {
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/MixedTimeseries/types.ts:21:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     19 | import {
235.3     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 21 |   AnnotationLayer,
235.3        |   ^^^^^^^^^^^^^^^^
235.3   > 22 |   TimeGranularity,
235.3        | ^^^^^^^^^^^^^^^^^^
235.3   > 23 |   QueryFormData,
235.3        | ^^^^^^^^^^^^^^^^^^
235.3   > 24 |   QueryFormColumn,
235.3        | ^^^^^^^^^^^^^^^^^^
235.3   > 25 |   ContributionType,
235.3        | ^^^^^^^^^^^^^^^^^^
235.3   > 26 |   TimeFormatter,
235.3        | ^^^^^^^^^^^^^^^^^^
235.3   > 27 |   AxisType,
235.3        | ^^^^^^^^^^^
235.3     28 | } from '@superset-ui/core';
235.3     29 | import {
235.3     30 |   BaseChartProps,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/MixedTimeseries/types.ts:22:3
235.3 TS2304: Cannot find name 'TimeGranularity'.
235.3     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3     21 |   AnnotationLayer,
235.3   > 22 |   TimeGranularity,
235.3        |   ^^^^^^^^^^^^^^^
235.3     23 |   QueryFormData,
235.3     24 |   QueryFormColumn,
235.3     25 |   ContributionType,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/MixedTimeseries/types.ts:23:3
235.3 TS2304: Cannot find name 'QueryFormData'.
235.3     21 |   AnnotationLayer,
235.3     22 |   TimeGranularity,
235.3   > 23 |   QueryFormData,
235.3        |   ^^^^^^^^^^^^^
235.3     24 |   QueryFormColumn,
235.3     25 |   ContributionType,
235.3     26 |   TimeFormatter,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/MixedTimeseries/types.ts:24:3
235.3 TS2304: Cannot find name 'QueryFormColumn'.
235.3     22 |   TimeGranularity,
235.3     23 |   QueryFormData,
235.3   > 24 |   QueryFormColumn,
235.3        |   ^^^^^^^^^^^^^^^
235.3     25 |   ContributionType,
235.3     26 |   TimeFormatter,
235.3     27 |   AxisType,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/MixedTimeseries/types.ts:25:3
235.3 TS2304: Cannot find name 'ContributionType'.
235.3     23 |   QueryFormData,
235.3     24 |   QueryFormColumn,
235.3   > 25 |   ContributionType,
235.3        |   ^^^^^^^^^^^^^^^^
235.3     26 |   TimeFormatter,
235.3     27 |   AxisType,
235.3     28 | } from '@superset-ui/core';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/MixedTimeseries/types.ts:26:3
235.3 TS2304: Cannot find name 'TimeFormatter'.
235.3     24 |   QueryFormColumn,
235.3     25 |   ContributionType,
235.3   > 26 |   TimeFormatter,
235.3        |   ^^^^^^^^^^^^^
235.3     27 |   AxisType,
235.3     28 | } from '@superset-ui/core';
235.3     29 | import {
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/MixedTimeseries/types.ts:27:3
235.3 TS2304: Cannot find name 'AxisType'.
235.3     25 |   ContributionType,
235.3     26 |   TimeFormatter,
235.3   > 27 |   AxisType,
235.3        |   ^^^^^^^^
235.3     28 | } from '@superset-ui/core';
235.3     29 | import {
235.3     30 |   BaseChartProps,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/MixedTimeseries/types.ts:28:3
235.3 TS2304: Cannot find name 'from'.
235.3     26 |   TimeFormatter,
235.3     27 |   AxisType,
235.3   > 28 | } from '@superset-ui/core';
235.3        |   ^^^^
235.3     29 | import {
235.3     30 |   BaseChartProps,
235.3     31 |   BaseTransformedProps,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/MixedTimeseries/types.ts:45:46
235.3 TS2304: Cannot find name 'QueryFormData'.
235.3     43 | } from '../constants';
235.3     44 |
235.3   > 45 | export type EchartsMixedTimeseriesFormData = QueryFormData & {
235.3        |                                              ^^^^^^^^^^^^^
235.3     46 |   annotationLayers: AnnotationLayer[];
235.3     47 |   // shared properties
235.3     48 |   minorSplitLine: boolean;
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/MixedTimeseries/types.ts:46:21
235.3 TS2304: Cannot find name 'AnnotationLayer'.
235.3     44 |
235.3     45 | export type EchartsMixedTimeseriesFormData = QueryFormData & {
235.3   > 46 |   annotationLayers: AnnotationLayer[];
235.3        |                     ^^^^^^^^^^^^^^^
235.3     47 |   // shared properties
235.3     48 |   minorSplitLine: boolean;
235.3     49 |   minorTicks: boolean;
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/MixedTimeseries/types.ts:60:19
235.3 TS2304: Cannot find name 'TimeGranularity'.
235.3     58 |   truncateYAxis: boolean;
235.3     59 |   truncateYAxisSecondary: boolean;
235.3   > 60 |   timeGrainSqla?: TimeGranularity;
235.3        |                   ^^^^^^^^^^^^^^^
235.3     61 |   tooltipTimeFormat?: string;
235.3     62 |   zoomable: boolean;
235.3     63 |   richTooltip: boolean;
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/MixedTimeseries/types.ts:70:22
235.3 TS2304: Cannot find name 'ContributionType'.
235.3     68 |   area: boolean;
235.3     69 |   areaB: boolean;
235.3   > 70 |   contributionMode?: ContributionType;
235.3        |                      ^^^^^^^^^^^^^^^^
235.3     71 |   contributionModeB?: ContributionType;
235.3     72 |   markerEnabled: boolean;
235.3     73 |   markerEnabledB: boolean;
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/MixedTimeseries/types.ts:71:23
235.3 TS2304: Cannot find name 'ContributionType'.
235.3     69 |   areaB: boolean;
235.3     70 |   contributionMode?: ContributionType;
235.3   > 71 |   contributionModeB?: ContributionType;
235.3        |                       ^^^^^^^^^^^^^^^^
235.3     72 |   markerEnabled: boolean;
235.3     73 |   markerEnabledB: boolean;
235.3     74 |   markerSize: number;
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/MixedTimeseries/types.ts:90:12
235.3 TS2304: Cannot find name 'QueryFormColumn'.
235.3     88 |   yAxisIndex?: number;
235.3     89 |   yAxisIndexB?: number;
235.3   > 90 |   groupby: QueryFormColumn[];
235.3        |            ^^^^^^^^^^^^^^^
235.3     91 |   groupbyB: QueryFormColumn[];
235.3     92 | } & LegendFormData &
235.3     93 |   TitleFormData;
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/MixedTimeseries/types.ts:91:13
235.3 TS2304: Cannot find name 'QueryFormColumn'.
235.3     89 |   yAxisIndexB?: number;
235.3     90 |   groupby: QueryFormColumn[];
235.3   > 91 |   groupbyB: QueryFormColumn[];
235.3        |             ^^^^^^^^^^^^^^^
235.3     92 | } & LegendFormData &
235.3     93 |   TitleFormData;
235.3     94 |
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/MixedTimeseries/types.ts:151:17
235.3 TS2304: Cannot find name 'QueryFormColumn'.
235.3     149 |     ContextMenuTransformedProps &
235.3     150 |     CrossFilterTransformedProps & {
235.3   > 151 |       groupbyB: QueryFormColumn[];
235.3         |                 ^^^^^^^^^^^^^^^
235.3     152 |       labelMapB: Record<string, string[]>;
235.3     153 |       seriesBreakdown: number;
235.3     154 |       xValueFormatter: TimeFormatter | StringConstructor;
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/MixedTimeseries/types.ts:154:24
235.3 TS2304: Cannot find name 'TimeFormatter'.
235.3     152 |       labelMapB: Record<string, string[]>;
235.3     153 |       seriesBreakdown: number;
235.3   > 154 |       xValueFormatter: TimeFormatter | StringConstructor;
235.3         |                        ^^^^^^^^^^^^^
235.3     155 |       xAxis: {
235.3     156 |         label: string;
235.3     157 |         type: AxisType;
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/MixedTimeseries/types.ts:157:15
235.3 TS2304: Cannot find name 'AxisType'.
235.3     155 |       xAxis: {
235.3     156 |         label: string;
235.3   > 157 |         type: AxisType;
235.3         |               ^^^^^^^^
235.3     158 |       };
235.3     159 |       onFocusedSeries: (series: string | null) => void;
235.3     160 |     };
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Pie/buildQuery.ts:20:8
235.3 TS1141: String literal expected.
235.3     18 |  */
235.3     19 | import {
235.3   > 20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3        |        ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     21 |   buildQueryContext,
235.3     22 |   getMetricLabel,
235.3     23 |   QueryFormData,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Pie/buildQuery.ts:20:118
235.3 TS2304: Cannot find name 'from'.
235.3     18 |  */
235.3     19 | import {
235.3   > 20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3        |                                                                                                                      ^^^^
235.3     21 |   buildQueryContext,
235.3     22 |   getMetricLabel,
235.3     23 |   QueryFormData,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Pie/buildQuery.ts:21:3
235.3 TS2304: Cannot find name 'buildQueryContext'.
235.3     19 | import {
235.3     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 21 |   buildQueryContext,
235.3        |   ^^^^^^^^^^^^^^^^^
235.3     22 |   getMetricLabel,
235.3     23 |   QueryFormData,
235.3     24 | } from '@superset-ui/core';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Pie/buildQuery.ts:21:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     19 | import {
235.3     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 21 |   buildQueryContext,
235.3        |   ^^^^^^^^^^^^^^^^^
235.3     22 |   getMetricLabel,
235.3     23 |   QueryFormData,
235.3     24 | } from '@superset-ui/core';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Pie/buildQuery.ts:21:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     19 | import {
235.3     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 21 |   buildQueryContext,
235.3        |   ^^^^^^^^^^^^^^^^^^
235.3   > 22 |   getMetricLabel,
235.3        | ^^^^^^^^^^^^^^^^^
235.3     23 |   QueryFormData,
235.3     24 | } from '@superset-ui/core';
235.3     25 | import { getContributionLabel } from './utils';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Pie/buildQuery.ts:21:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     19 | import {
235.3     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 21 |   buildQueryContext,
235.3        |   ^^^^^^^^^^^^^^^^^^
235.3   > 22 |   getMetricLabel,
235.3        | ^^^^^^^^^^^^^^^^^
235.3   > 23 |   QueryFormData,
235.3        | ^^^^^^^^^^^^^^^^
235.3     24 | } from '@superset-ui/core';
235.3     25 | import { getContributionLabel } from './utils';
235.3     26 |
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Pie/buildQuery.ts:22:3
235.3 TS2304: Cannot find name 'getMetricLabel'.
235.3     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3     21 |   buildQueryContext,
235.3   > 22 |   getMetricLabel,
235.3        |   ^^^^^^^^^^^^^^
235.3     23 |   QueryFormData,
235.3     24 | } from '@superset-ui/core';
235.3     25 | import { getContributionLabel } from './utils';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Pie/buildQuery.ts:23:3
235.3 TS2304: Cannot find name 'QueryFormData'.
235.3     21 |   buildQueryContext,
235.3     22 |   getMetricLabel,
235.3   > 23 |   QueryFormData,
235.3        |   ^^^^^^^^^^^^^
235.3     24 | } from '@superset-ui/core';
235.3     25 | import { getContributionLabel } from './utils';
235.3     26 |
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Pie/buildQuery.ts:24:3
235.3 TS2304: Cannot find name 'from'.
235.3     22 |   getMetricLabel,
235.3     23 |   QueryFormData,
235.3   > 24 | } from '@superset-ui/core';
235.3        |   ^^^^
235.3     25 | import { getContributionLabel } from './utils';
235.3     26 |
235.3     27 | export default function buildQuery(formData: QueryFormData) {
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Pie/buildQuery.ts:27:46
235.3 TS2304: Cannot find name 'QueryFormData'.
235.3     25 | import { getContributionLabel } from './utils';
235.3     26 |
235.3   > 27 | export default function buildQuery(formData: QueryFormData) {
235.3        |                                              ^^^^^^^^^^^^^
235.3     28 |   const { metric, sort_by_metric } = formData;
235.3     29 |   const metricLabel = getMetricLabel(metric);
235.3     30 |
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Pie/buildQuery.ts:29:23
235.3 TS2304: Cannot find name 'getMetricLabel'.
235.3     27 | export default function buildQuery(formData: QueryFormData) {
235.3     28 |   const { metric, sort_by_metric } = formData;
235.3   > 29 |   const metricLabel = getMetricLabel(metric);
235.3        |                       ^^^^^^^^^^^^^^
235.3     30 |
235.3     31 |   return buildQueryContext(formData, baseQueryObject => [
235.3     32 |     {
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Pie/buildQuery.ts:31:10
235.3 TS2304: Cannot find name 'buildQueryContext'.
235.3     29 |   const metricLabel = getMetricLabel(metric);
235.3     30 |
235.3   > 31 |   return buildQueryContext(formData, baseQueryObject => [
235.3        |          ^^^^^^^^^^^^^^^^^
235.3     32 |     {
235.3     33 |       ...baseQueryObject,
235.3     34 |       ...(sort_by_metric && { orderby: [[metric, false]] }),
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Pie/index.ts:33:3
235.3 TS2344: Type 'EchartsPieChartProps' does not satisfy the constraint 'ChartProps<PlainObject>'.
235.3   Type 'EchartsPieChartProps' is missing the following properties from type 'ChartProps<PlainObject>': annotationData, datasource, rawDatasource, initialValues, and 9 more.
235.3     31 | export default class EchartsPieChartPlugin extends EchartsChartPlugin<
235.3     32 |   EchartsPieFormData,
235.3   > 33 |   EchartsPieChartProps
235.3        |   ^^^^^^^^^^^^^^^^^^^^
235.3     34 | > {
235.3     35 |   /**
235.3     36 |    * The constructor is used to pass relevant metadata and callbacks that get
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Pie/transformProps.ts:128:5
235.3 TS2339: Property 'height' does not exist on type 'EchartsPieChartProps'.
235.3     126 |   const {
235.3     127 |     formData,
235.3   > 128 |     height,
235.3         |     ^^^^^^
235.3     129 |     hooks,
235.3     130 |     filterState,
235.3     131 |     queriesData,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Pie/transformProps.ts:129:5
235.3 TS2339: Property 'hooks' does not exist on type 'EchartsPieChartProps'.
235.3     127 |     formData,
235.3     128 |     height,
235.3   > 129 |     hooks,
235.3         |     ^^^^^
235.3     130 |     filterState,
235.3     131 |     queriesData,
235.3     132 |     width,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Pie/transformProps.ts:130:5
235.3 TS2339: Property 'filterState' does not exist on type 'EchartsPieChartProps'.
235.3     128 |     height,
235.3     129 |     hooks,
235.3   > 130 |     filterState,
235.3         |     ^^^^^^^^^^^
235.3     131 |     queriesData,
235.3     132 |     width,
235.3     133 |     theme,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Pie/transformProps.ts:131:5
235.3 TS2339: Property 'queriesData' does not exist on type 'EchartsPieChartProps'.
235.3     129 |     hooks,
235.3     130 |     filterState,
235.3   > 131 |     queriesData,
235.3         |     ^^^^^^^^^^^
235.3     132 |     width,
235.3     133 |     theme,
235.3     134 |     inContextMenu,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Pie/transformProps.ts:132:5
235.3 TS2339: Property 'width' does not exist on type 'EchartsPieChartProps'.
235.3     130 |     filterState,
235.3     131 |     queriesData,
235.3   > 132 |     width,
235.3         |     ^^^^^
235.3     133 |     theme,
235.3     134 |     inContextMenu,
235.3     135 |     emitCrossFilters,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Pie/transformProps.ts:133:5
235.3 TS2339: Property 'theme' does not exist on type 'EchartsPieChartProps'.
235.3     131 |     queriesData,
235.3     132 |     width,
235.3   > 133 |     theme,
235.3         |     ^^^^^
235.3     134 |     inContextMenu,
235.3     135 |     emitCrossFilters,
235.3     136 |     datasource,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Pie/transformProps.ts:134:5
235.3 TS2339: Property 'inContextMenu' does not exist on type 'EchartsPieChartProps'.
235.3     132 |     width,
235.3     133 |     theme,
235.3   > 134 |     inContextMenu,
235.3         |     ^^^^^^^^^^^^^
235.3     135 |     emitCrossFilters,
235.3     136 |     datasource,
235.3     137 |   } = chartProps;
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Pie/transformProps.ts:135:5
235.3 TS2339: Property 'emitCrossFilters' does not exist on type 'EchartsPieChartProps'.
235.3     133 |     theme,
235.3     134 |     inContextMenu,
235.3   > 135 |     emitCrossFilters,
235.3         |     ^^^^^^^^^^^^^^^^
235.3     136 |     datasource,
235.3     137 |   } = chartProps;
235.3     138 |   const { columnFormats = {}, currencyFormats = {} } = datasource;
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Pie/transformProps.ts:136:5
235.3 TS2339: Property 'datasource' does not exist on type 'EchartsPieChartProps'.
235.3     134 |     inContextMenu,
235.3     135 |     emitCrossFilters,
235.3   > 136 |     datasource,
235.3         |     ^^^^^^^^^^
235.3     137 |   } = chartProps;
235.3     138 |   const { columnFormats = {}, currencyFormats = {} } = datasource;
235.3     139 |   const { data: rawData = [] } = queriesData[0];
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Pie/types.ts:21:8
235.3 TS1141: String literal expected.
235.3     19 | import { QueryFormColumn, QueryFormData } from '@superset-ui/core';
235.3     20 | import {
235.3   > 21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3        |        ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     22 |   BaseChartProps,
235.3     23 |   BaseTransformedProps,
235.3     24 |   ContextMenuTransformedProps,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Pie/types.ts:21:118
235.3 TS2304: Cannot find name 'from'.
235.3     19 | import { QueryFormColumn, QueryFormData } from '@superset-ui/core';
235.3     20 | import {
235.3   > 21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3        |                                                                                                                      ^^^^
235.3     22 |   BaseChartProps,
235.3     23 |   BaseTransformedProps,
235.3     24 |   ContextMenuTransformedProps,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Pie/types.ts:22:3
235.3 TS2304: Cannot find name 'BaseChartProps'.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   BaseChartProps,
235.3        |   ^^^^^^^^^^^^^^
235.3     23 |   BaseTransformedProps,
235.3     24 |   ContextMenuTransformedProps,
235.3     25 |   CrossFilterTransformedProps,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Pie/types.ts:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   BaseChartProps,
235.3        |   ^^^^^^^^^^^^^^
235.3     23 |   BaseTransformedProps,
235.3     24 |   ContextMenuTransformedProps,
235.3     25 |   CrossFilterTransformedProps,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Pie/types.ts:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   BaseChartProps,
235.3        |   ^^^^^^^^^^^^^^^
235.3   > 23 |   BaseTransformedProps,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^
235.3     24 |   ContextMenuTransformedProps,
235.3     25 |   CrossFilterTransformedProps,
235.3     26 |   LegendFormData,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Pie/types.ts:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   BaseChartProps,
235.3        |   ^^^^^^^^^^^^^^^
235.3   > 23 |   BaseTransformedProps,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 24 |   ContextMenuTransformedProps,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     25 |   CrossFilterTransformedProps,
235.3     26 |   LegendFormData,
235.3     27 |   LegendOrientation,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Pie/types.ts:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   BaseChartProps,
235.3        |   ^^^^^^^^^^^^^^^
235.3   > 23 |   BaseTransformedProps,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 24 |   ContextMenuTransformedProps,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 25 |   CrossFilterTransformedProps,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     26 |   LegendFormData,
235.3     27 |   LegendOrientation,
235.3     28 |   LegendType,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Pie/types.ts:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   BaseChartProps,
235.3        |   ^^^^^^^^^^^^^^^
235.3   > 23 |   BaseTransformedProps,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 24 |   ContextMenuTransformedProps,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 25 |   CrossFilterTransformedProps,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 26 |   LegendFormData,
235.3        | ^^^^^^^^^^^^^^^^^
235.3     27 |   LegendOrientation,
235.3     28 |   LegendType,
235.3     29 | } from '../types';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Pie/types.ts:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   BaseChartProps,
235.3        |   ^^^^^^^^^^^^^^^
235.3   > 23 |   BaseTransformedProps,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 24 |   ContextMenuTransformedProps,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 25 |   CrossFilterTransformedProps,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 26 |   LegendFormData,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 27 |   LegendOrientation,
235.3        | ^^^^^^^^^^^^^^^^^^^^
235.3     28 |   LegendType,
235.3     29 | } from '../types';
235.3     30 | import { DEFAULT_LEGEND_FORM_DATA } from '../constants';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Pie/types.ts:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   BaseChartProps,
235.3        |   ^^^^^^^^^^^^^^^
235.3   > 23 |   BaseTransformedProps,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 24 |   ContextMenuTransformedProps,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 25 |   CrossFilterTransformedProps,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 26 |   LegendFormData,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 27 |   LegendOrientation,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 28 |   LegendType,
235.3        | ^^^^^^^^^^^^^
235.3     29 | } from '../types';
235.3     30 | import { DEFAULT_LEGEND_FORM_DATA } from '../constants';
235.3     31 |
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Pie/types.ts:23:3
235.3 TS2304: Cannot find name 'BaseTransformedProps'.
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3     22 |   BaseChartProps,
235.3   > 23 |   BaseTransformedProps,
235.3        |   ^^^^^^^^^^^^^^^^^^^^
235.3     24 |   ContextMenuTransformedProps,
235.3     25 |   CrossFilterTransformedProps,
235.3     26 |   LegendFormData,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Pie/types.ts:24:3
235.3 TS2304: Cannot find name 'ContextMenuTransformedProps'.
235.3     22 |   BaseChartProps,
235.3     23 |   BaseTransformedProps,
235.3   > 24 |   ContextMenuTransformedProps,
235.3        |   ^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     25 |   CrossFilterTransformedProps,
235.3     26 |   LegendFormData,
235.3     27 |   LegendOrientation,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Pie/types.ts:25:3
235.3 TS2304: Cannot find name 'CrossFilterTransformedProps'.
235.3     23 |   BaseTransformedProps,
235.3     24 |   ContextMenuTransformedProps,
235.3   > 25 |   CrossFilterTransformedProps,
235.3        |   ^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     26 |   LegendFormData,
235.3     27 |   LegendOrientation,
235.3     28 |   LegendType,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Pie/types.ts:26:3
235.3 TS2304: Cannot find name 'LegendFormData'.
235.3     24 |   ContextMenuTransformedProps,
235.3     25 |   CrossFilterTransformedProps,
235.3   > 26 |   LegendFormData,
235.3        |   ^^^^^^^^^^^^^^
235.3     27 |   LegendOrientation,
235.3     28 |   LegendType,
235.3     29 | } from '../types';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Pie/types.ts:27:3
235.3 TS2304: Cannot find name 'LegendOrientation'.
235.3     25 |   CrossFilterTransformedProps,
235.3     26 |   LegendFormData,
235.3   > 27 |   LegendOrientation,
235.3        |   ^^^^^^^^^^^^^^^^^
235.3     28 |   LegendType,
235.3     29 | } from '../types';
235.3     30 | import { DEFAULT_LEGEND_FORM_DATA } from '../constants';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Pie/types.ts:28:3
235.3 TS2304: Cannot find name 'LegendType'.
235.3     26 |   LegendFormData,
235.3     27 |   LegendOrientation,
235.3   > 28 |   LegendType,
235.3        |   ^^^^^^^^^^
235.3     29 | } from '../types';
235.3     30 | import { DEFAULT_LEGEND_FORM_DATA } from '../constants';
235.3     31 |
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Pie/types.ts:29:3
235.3 TS2304: Cannot find name 'from'.
235.3     27 |   LegendOrientation,
235.3     28 |   LegendType,
235.3   > 29 | } from '../types';
235.3        |   ^^^^
235.3     30 | import { DEFAULT_LEGEND_FORM_DATA } from '../constants';
235.3     31 |
235.3     32 | export type EchartsPieFormData = QueryFormData &
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Pie/types.ts:33:3
235.3 TS2304: Cannot find name 'LegendFormData'.
235.3     31 |
235.3     32 | export type EchartsPieFormData = QueryFormData &
235.3   > 33 |   LegendFormData & {
235.3        |   ^^^^^^^^^^^^^^
235.3     34 |     colorScheme?: string;
235.3     35 |     currentOwnValue?: string[] | null;
235.3     36 |     donut: boolean;
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Pie/types.ts:66:11
235.3 TS2304: Cannot find name 'BaseChartProps'.
235.3     64 |
235.3     65 | export interface EchartsPieChartProps
235.3   > 66 |   extends BaseChartProps<EchartsPieFormData> {
235.3        |           ^^^^^^^^^^^^^^
235.3     67 |   formData: EchartsPieFormData;
235.3     68 | }
235.3     69 |
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Pie/types.ts:78:22
235.3 TS2304: Cannot find name 'LegendOrientation'.
235.3     76 |   labelLine: false,
235.3     77 |   labelType: EchartsPieLabelType.Key,
235.3   > 78 |   legendOrientation: LegendOrientation.Top,
235.3        |                      ^^^^^^^^^^^^^^^^^
235.3     79 |   legendType: LegendType.Scroll,
235.3     80 |   numberFormat: 'SMART_NUMBER',
235.3     81 |   outerRadius: 70,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Pie/types.ts:79:15
235.3 TS2304: Cannot find name 'LegendType'.
235.3     77 |   labelType: EchartsPieLabelType.Key,
235.3     78 |   legendOrientation: LegendOrientation.Top,
235.3   > 79 |   legendType: LegendType.Scroll,
235.3        |               ^^^^^^^^^^
235.3     80 |   numberFormat: 'SMART_NUMBER',
235.3     81 |   outerRadius: 70,
235.3     82 |   showLabels: true,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Pie/types.ts:91:3
235.3 TS2304: Cannot find name 'BaseTransformedProps'.
235.3     89 |
235.3     90 | export type PieChartTransformedProps =
235.3   > 91 |   BaseTransformedProps<EchartsPieFormData> &
235.3        |   ^^^^^^^^^^^^^^^^^^^^
235.3     92 |     ContextMenuTransformedProps &
235.3     93 |     CrossFilterTransformedProps;
235.3     94 |
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Pie/types.ts:92:5
235.3 TS2304: Cannot find name 'ContextMenuTransformedProps'.
235.3     90 | export type PieChartTransformedProps =
235.3     91 |   BaseTransformedProps<EchartsPieFormData> &
235.3   > 92 |     ContextMenuTransformedProps &
235.3        |     ^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     93 |     CrossFilterTransformedProps;
235.3     94 |
235.3     95 | export interface PieChartDataItem {
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Pie/types.ts:93:5
235.3 TS2304: Cannot find name 'CrossFilterTransformedProps'.
235.3     91 |   BaseTransformedProps<EchartsPieFormData> &
235.3     92 |     ContextMenuTransformedProps &
235.3   > 93 |     CrossFilterTransformedProps;
235.3        |     ^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     94 |
235.3     95 | export interface PieChartDataItem {
235.3     96 |   name: string;
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/buildQuery.ts:20:8
235.3 TS1141: String literal expected.
235.3     18 |  */
235.3     19 | import {
235.3   > 20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3        |        ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     21 |   buildQueryContext,
235.3     22 |   QueryFormData,
235.3     23 |   ensureIsArray,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/buildQuery.ts:20:118
235.3 TS2304: Cannot find name 'from'.
235.3     18 |  */
235.3     19 | import {
235.3   > 20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3        |                                                                                                                      ^^^^
235.3     21 |   buildQueryContext,
235.3     22 |   QueryFormData,
235.3     23 |   ensureIsArray,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/buildQuery.ts:21:3
235.3 TS2304: Cannot find name 'buildQueryContext'.
235.3     19 | import {
235.3     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 21 |   buildQueryContext,
235.3        |   ^^^^^^^^^^^^^^^^^
235.3     22 |   QueryFormData,
235.3     23 |   ensureIsArray,
235.3     24 | } from '@superset-ui/core';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/buildQuery.ts:21:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     19 | import {
235.3     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 21 |   buildQueryContext,
235.3        |   ^^^^^^^^^^^^^^^^^
235.3     22 |   QueryFormData,
235.3     23 |   ensureIsArray,
235.3     24 | } from '@superset-ui/core';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/buildQuery.ts:21:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     19 | import {
235.3     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 21 |   buildQueryContext,
235.3        |   ^^^^^^^^^^^^^^^^^^
235.3   > 22 |   QueryFormData,
235.3        | ^^^^^^^^^^^^^^^^
235.3     23 |   ensureIsArray,
235.3     24 | } from '@superset-ui/core';
235.3     25 |
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/buildQuery.ts:21:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     19 | import {
235.3     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 21 |   buildQueryContext,
235.3        |   ^^^^^^^^^^^^^^^^^^
235.3   > 22 |   QueryFormData,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 23 |   ensureIsArray,
235.3        | ^^^^^^^^^^^^^^^^
235.3     24 | } from '@superset-ui/core';
235.3     25 |
235.3     26 | export default function buildQuery(formData: QueryFormData) {
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/buildQuery.ts:22:3
235.3 TS2304: Cannot find name 'QueryFormData'.
235.3     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3     21 |   buildQueryContext,
235.3   > 22 |   QueryFormData,
235.3        |   ^^^^^^^^^^^^^
235.3     23 |   ensureIsArray,
235.3     24 | } from '@superset-ui/core';
235.3     25 |
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/buildQuery.ts:23:3
235.3 TS2304: Cannot find name 'ensureIsArray'.
235.3     21 |   buildQueryContext,
235.3     22 |   QueryFormData,
235.3   > 23 |   ensureIsArray,
235.3        |   ^^^^^^^^^^^^^
235.3     24 | } from '@superset-ui/core';
235.3     25 |
235.3     26 | export default function buildQuery(formData: QueryFormData) {
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/buildQuery.ts:24:3
235.3 TS2304: Cannot find name 'from'.
235.3     22 |   QueryFormData,
235.3     23 |   ensureIsArray,
235.3   > 24 | } from '@superset-ui/core';
235.3        |   ^^^^
235.3     25 |
235.3     26 | export default function buildQuery(formData: QueryFormData) {
235.3     27 |   const { series_limit_metric } = formData;
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/buildQuery.ts:26:46
235.3 TS2304: Cannot find name 'QueryFormData'.
235.3     24 | } from '@superset-ui/core';
235.3     25 |
235.3   > 26 | export default function buildQuery(formData: QueryFormData) {
235.3        |                                              ^^^^^^^^^^^^^
235.3     27 |   const { series_limit_metric } = formData;
235.3     28 |   const sortByMetric = ensureIsArray(series_limit_metric)[0];
235.3     29 |
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/buildQuery.ts:28:24
235.3 TS2304: Cannot find name 'ensureIsArray'.
235.3     26 | export default function buildQuery(formData: QueryFormData) {
235.3     27 |   const { series_limit_metric } = formData;
235.3   > 28 |   const sortByMetric = ensureIsArray(series_limit_metric)[0];
235.3        |                        ^^^^^^^^^^^^^
235.3     29 |
235.3     30 |   return buildQueryContext(formData, baseQueryObject => {
235.3     31 |     let { metrics, orderby = [] } = baseQueryObject;
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/buildQuery.ts:30:10
235.3 TS2304: Cannot find name 'buildQueryContext'.
235.3     28 |   const sortByMetric = ensureIsArray(series_limit_metric)[0];
235.3     29 |
235.3   > 30 |   return buildQueryContext(formData, baseQueryObject => {
235.3        |          ^^^^^^^^^^^^^^^^^
235.3     31 |     let { metrics, orderby = [] } = baseQueryObject;
235.3     32 |     metrics = metrics || [];
235.3     33 |     // override orderby with timeseries metric
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/controlPanel.tsx:20:8
235.3 TS1141: String literal expected.
235.3     18 |  */
235.3     19 | import {
235.3   > 20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3        |        ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     21 |   ChartDataResponseResult,
235.3     22 |   GenericDataType,
235.3     23 |   QueryFormMetric,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/controlPanel.tsx:20:118
235.3 TS2304: Cannot find name 'from'.
235.3     18 |  */
235.3     19 | import {
235.3   > 20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3        |                                                                                                                      ^^^^
235.3     21 |   ChartDataResponseResult,
235.3     22 |   GenericDataType,
235.3     23 |   QueryFormMetric,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/controlPanel.tsx:21:3
235.3 TS2304: Cannot find name 'ChartDataResponseResult'.
235.3     19 | import {
235.3     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 21 |   ChartDataResponseResult,
235.3        |   ^^^^^^^^^^^^^^^^^^^^^^^
235.3     22 |   GenericDataType,
235.3     23 |   QueryFormMetric,
235.3     24 |   t,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/controlPanel.tsx:21:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     19 | import {
235.3     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 21 |   ChartDataResponseResult,
235.3        |   ^^^^^^^^^^^^^^^^^^^^^^^
235.3     22 |   GenericDataType,
235.3     23 |   QueryFormMetric,
235.3     24 |   t,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/controlPanel.tsx:21:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     19 | import {
235.3     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 21 |   ChartDataResponseResult,
235.3        |   ^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 22 |   GenericDataType,
235.3        | ^^^^^^^^^^^^^^^^^^
235.3     23 |   QueryFormMetric,
235.3     24 |   t,
235.3     25 |   validateNumber,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/controlPanel.tsx:21:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     19 | import {
235.3     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 21 |   ChartDataResponseResult,
235.3        |   ^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 22 |   GenericDataType,
235.3        | ^^^^^^^^^^^^^^^^^^
235.3   > 23 |   QueryFormMetric,
235.3        | ^^^^^^^^^^^^^^^^^^
235.3     24 |   t,
235.3     25 |   validateNumber,
235.3     26 | } from '@superset-ui/core';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/controlPanel.tsx:21:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     19 | import {
235.3     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 21 |   ChartDataResponseResult,
235.3        |   ^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 22 |   GenericDataType,
235.3        | ^^^^^^^^^^^^^^^^^^
235.3   > 23 |   QueryFormMetric,
235.3        | ^^^^^^^^^^^^^^^^^^
235.3   > 24 |   t,
235.3        | ^^^^
235.3     25 |   validateNumber,
235.3     26 | } from '@superset-ui/core';
235.3     27 | import {
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/controlPanel.tsx:21:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     19 | import {
235.3     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 21 |   ChartDataResponseResult,
235.3        |   ^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 22 |   GenericDataType,
235.3        | ^^^^^^^^^^^^^^^^^^
235.3   > 23 |   QueryFormMetric,
235.3        | ^^^^^^^^^^^^^^^^^^
235.3   > 24 |   t,
235.3        | ^^^^^^^^^^^^^^^^^^
235.3   > 25 |   validateNumber,
235.3        | ^^^^^^^^^^^^^^^^^
235.3     26 | } from '@superset-ui/core';
235.3     27 | import {
235.3     28 |   ControlPanelConfig,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/controlPanel.tsx:22:3
235.3 TS2304: Cannot find name 'GenericDataType'.
235.3     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3     21 |   ChartDataResponseResult,
235.3   > 22 |   GenericDataType,
235.3        |   ^^^^^^^^^^^^^^^
235.3     23 |   QueryFormMetric,
235.3     24 |   t,
235.3     25 |   validateNumber,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/controlPanel.tsx:23:3
235.3 TS2304: Cannot find name 'QueryFormMetric'.
235.3     21 |   ChartDataResponseResult,
235.3     22 |   GenericDataType,
235.3   > 23 |   QueryFormMetric,
235.3        |   ^^^^^^^^^^^^^^^
235.3     24 |   t,
235.3     25 |   validateNumber,
235.3     26 | } from '@superset-ui/core';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/controlPanel.tsx:24:3
235.3 TS2304: Cannot find name 't'.
235.3     22 |   GenericDataType,
235.3     23 |   QueryFormMetric,
235.3   > 24 |   t,
235.3        |   ^
235.3     25 |   validateNumber,
235.3     26 | } from '@superset-ui/core';
235.3     27 | import {
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/controlPanel.tsx:25:3
235.3 TS2304: Cannot find name 'validateNumber'.
235.3     23 |   QueryFormMetric,
235.3     24 |   t,
235.3   > 25 |   validateNumber,
235.3        |   ^^^^^^^^^^^^^^
235.3     26 | } from '@superset-ui/core';
235.3     27 | import {
235.3     28 |   ControlPanelConfig,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/controlPanel.tsx:26:3
235.3 TS2304: Cannot find name 'from'.
235.3     24 |   t,
235.3     25 |   validateNumber,
235.3   > 26 | } from '@superset-ui/core';
235.3        |   ^^^^
235.3     27 | import {
235.3     28 |   ControlPanelConfig,
235.3     29 |   ControlSubSectionHeader,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/controlPanel.tsx:49:12
235.3 TS2304: Cannot find name 't'.
235.3     47 |   config: {
235.3     48 |     controlType: 'InputNumber',
235.3   > 49 |     label: t('Max'),
235.3        |            ^
235.3     50 |     description: t(
235.3     51 |       'The maximum value of metrics. It is an optional configuration',
235.3     52 |     ),
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/controlPanel.tsx:50:18
235.3 TS2304: Cannot find name 't'.
235.3     48 |     controlType: 'InputNumber',
235.3     49 |     label: t('Max'),
235.3   > 50 |     description: t(
235.3        |                  ^
235.3     51 |       'The maximum value of metrics. It is an optional configuration',
235.3     52 |     ),
235.3     53 |     width: 120,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/controlPanel.tsx:54:18
235.3 TS2304: Cannot find name 't'.
235.3     52 |     ),
235.3     53 |     width: 120,
235.3   > 54 |     placeholder: t('auto'),
235.3        |                  ^
235.3     55 |     debounceDelay: 400,
235.3     56 |     validators: [validateNumber],
235.3     57 |   },
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/controlPanel.tsx:56:18
235.3 TS2304: Cannot find name 'validateNumber'.
235.3     54 |     placeholder: t('auto'),
235.3     55 |     debounceDelay: 400,
235.3   > 56 |     validators: [validateNumber],
235.3        |                  ^^^^^^^^^^^^^^
235.3     57 |   },
235.3     58 | };
235.3     59 |
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/controlPanel.tsx:64:12
235.3 TS2304: Cannot find name 't'.
235.3     62 |   config: {
235.3     63 |     controlType: 'InputNumber',
235.3   > 64 |     label: t('Min'),
235.3        |            ^
235.3     65 |     description: t(
235.3     66 |       'The minimum value of metrics. It is an optional configuration. If not set, it will be the minimum value of the data',
235.3     67 |     ),
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/controlPanel.tsx:65:18
235.3 TS2304: Cannot find name 't'.
235.3     63 |     controlType: 'InputNumber',
235.3     64 |     label: t('Min'),
235.3   > 65 |     description: t(
235.3        |                  ^
235.3     66 |       'The minimum value of metrics. It is an optional configuration. If not set, it will be the minimum value of the data',
235.3     67 |     ),
235.3     68 |     defaultValue: '0',
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/controlPanel.tsx:70:18
235.3 TS2304: Cannot find name 't'.
235.3     68 |     defaultValue: '0',
235.3     69 |     width: 120,
235.3   > 70 |     placeholder: t('auto'),
235.3        |                  ^
235.3     71 |     debounceDelay: 400,
235.3     72 |     validators: [validateNumber],
235.3     73 |   },
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/controlPanel.tsx:72:18
235.3 TS2304: Cannot find name 'validateNumber'.
235.3     70 |     placeholder: t('auto'),
235.3     71 |     debounceDelay: 400,
235.3   > 72 |     validators: [validateNumber],
235.3        |                  ^^^^^^^^^^^^^^
235.3     73 |   },
235.3     74 | };
235.3     75 |
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/controlPanel.tsx:79:14
235.3 TS2304: Cannot find name 't'.
235.3     77 |   controlPanelSections: [
235.3     78 |     {
235.3   > 79 |       label: t('Query'),
235.3        |              ^
235.3     80 |       expanded: true,
235.3     81 |       controlSetRows: [
235.3     82 |         ['groupby'],
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/controlPanel.tsx:98:14
235.3 TS2304: Cannot find name 't'.
235.3      96 |     },
235.3      97 |     {
235.3   >  98 |       label: t('Chart Options'),
235.3         |              ^
235.3      99 |       expanded: true,
235.3     100 |       controlSetRows: [
235.3     101 |         ['color_scheme'],
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/controlPanel.tsx:103:36
235.3 TS2304: Cannot find name 't'.
235.3     101 |         ['color_scheme'],
235.3     102 |         ...legendSection,
235.3   > 103 |         [<ControlSubSectionHeader>{t('Labels')}</ControlSubSectionHeader>],
235.3         |                                    ^
235.3     104 |         [
235.3     105 |           {
235.3     106 |             name: 'show_labels',
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/controlPanel.tsx:109:22
235.3 TS2304: Cannot find name 't'.
235.3     107 |             config: {
235.3     108 |               type: 'CheckboxControl',
235.3   > 109 |               label: t('Show Labels'),
235.3         |                      ^
235.3     110 |               renderTrigger: true,
235.3     111 |               default: showLabels,
235.3     112 |               description: t('Whether to display the labels.'),
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/controlPanel.tsx:112:28
235.3 TS2304: Cannot find name 't'.
235.3     110 |               renderTrigger: true,
235.3     111 |               default: showLabels,
235.3   > 112 |               description: t('Whether to display the labels.'),
235.3         |                            ^
235.3     113 |             },
235.3     114 |           },
235.3     115 |         ],
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/controlPanel.tsx:121:22
235.3 TS2304: Cannot find name 't'.
235.3     119 |             config: {
235.3     120 |               type: 'SelectControl',
235.3   > 121 |               label: t('Label Type'),
235.3         |                      ^
235.3     122 |               default: labelType,
235.3     123 |               renderTrigger: true,
235.3     124 |               choices: [
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/controlPanel.tsx:125:27
235.3 TS2304: Cannot find name 't'.
235.3     123 |               renderTrigger: true,
235.3     124 |               choices: [
235.3   > 125 |                 ['value', t('Value')],
235.3         |                           ^
235.3     126 |                 ['key_value', t('Category and Value')],
235.3     127 |               ],
235.3     128 |               description: t('What should be shown on the label?'),
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/controlPanel.tsx:126:31
235.3 TS2304: Cannot find name 't'.
235.3     124 |               choices: [
235.3     125 |                 ['value', t('Value')],
235.3   > 126 |                 ['key_value', t('Category and Value')],
235.3         |                               ^
235.3     127 |               ],
235.3     128 |               description: t('What should be shown on the label?'),
235.3     129 |             },
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/controlPanel.tsx:128:28
235.3 TS2304: Cannot find name 't'.
235.3     126 |                 ['key_value', t('Category and Value')],
235.3     127 |               ],
235.3   > 128 |               description: t('What should be shown on the label?'),
235.3         |                            ^
235.3     129 |             },
235.3     130 |           },
235.3     131 |         ],
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/controlPanel.tsx:138:22
235.3 TS2304: Cannot find name 't'.
235.3     136 |               type: 'SelectControl',
235.3     137 |               freeForm: false,
235.3   > 138 |               label: t('Label position'),
235.3         |                      ^
235.3     139 |               renderTrigger: true,
235.3     140 |               choices: LABEL_POSITION,
235.3     141 |               default: labelPosition,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/controlPanel.tsx:152:22
235.3 TS2304: Cannot find name 't'.
235.3     150 |               type: 'SelectControl',
235.3     151 |               freeForm: true,
235.3   > 152 |               label: t('Number format'),
235.3         |                      ^
235.3     153 |               renderTrigger: true,
235.3     154 |               default: numberFormat,
235.3     155 |               choices: D3_FORMAT_OPTIONS,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/controlPanel.tsx:166:22
235.3 TS2304: Cannot find name 't'.
235.3     164 |               type: 'SelectControl',
235.3     165 |               freeForm: true,
235.3   > 166 |               label: t('Date format'),
235.3         |                      ^
235.3     167 |               renderTrigger: true,
235.3     168 |               choices: D3_TIME_FORMAT_OPTIONS,
235.3     169 |               default: 'smart_date',
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/controlPanel.tsx:174:36
235.3 TS2304: Cannot find name 't'.
235.3     172 |           },
235.3     173 |         ],
235.3   > 174 |         [<ControlSubSectionHeader>{t('Radar')}</ControlSubSectionHeader>],
235.3         |                                    ^
235.3     175 |         [
235.3     176 |           {
235.3     177 |             name: 'column_config',
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/controlPanel.tsx:180:22
235.3 TS2304: Cannot find name 't'.
235.3     178 |             config: {
235.3     179 |               type: 'ColumnConfigControl',
235.3   > 180 |               label: t('Customize Metrics'),
235.3         |                      ^
235.3     181 |               description: t('Further customize how to display each metric'),
235.3     182 |               renderTrigger: true,
235.3     183 |               configFormLayout: {
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/controlPanel.tsx:181:28
235.3 TS2304: Cannot find name 't'.
235.3     179 |               type: 'ColumnConfigControl',
235.3     180 |               label: t('Customize Metrics'),
235.3   > 181 |               description: t('Further customize how to display each metric'),
235.3         |                            ^
235.3     182 |               renderTrigger: true,
235.3     183 |               configFormLayout: {
235.3     184 |                 [GenericDataType.Numeric]: [
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/controlPanel.tsx:184:18
235.3 TS2304: Cannot find name 'GenericDataType'.
235.3     182 |               renderTrigger: true,
235.3     183 |               configFormLayout: {
235.3   > 184 |                 [GenericDataType.Numeric]: [
235.3         |                  ^^^^^^^^^^^^^^^
235.3     185 |                   [radarMetricMinValue, radarMetricMaxValue],
235.3     186 |                 ],
235.3     187 |               },
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/controlPanel.tsx:193:57
235.3 TS2304: Cannot find name 'QueryFormMetric'.
235.3     191 |               mapStateToProps(explore, _, chart) {
235.3     192 |                 const values =
235.3   > 193 |                   (explore?.controls?.metrics?.value as QueryFormMetric[]) ??
235.3         |                                                         ^^^^^^^^^^^^^^^
235.3     194 |                   [];
235.3     195 |                 const metricColumn = values.map(value => {
235.3     196 |                   if (typeof value === 'string') {
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/controlPanel.tsx:204:33
235.3 TS2304: Cannot find name 'GenericDataType'.
235.3     202 |                   chart?.queriesResponse?.[0] ?? {};
235.3     203 |                 const colnames: string[] = _colnames || [];
235.3   > 204 |                 const coltypes: GenericDataType[] = _coltypes || [];
235.3         |                                 ^^^^^^^^^^^^^^^
235.3     205 |
235.3     206 |                 return {
235.3     207 |                   queryResponse: chart?.queriesResponse?.[0] as
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/controlPanel.tsx:208:23
235.3 TS2304: Cannot find name 'ChartDataResponseResult'.
235.3     206 |                 return {
235.3     207 |                   queryResponse: chart?.queriesResponse?.[0] as
235.3   > 208 |                     | ChartDataResponseResult
235.3         |                       ^^^^^^^^^^^^^^^^^^^^^^^
235.3     209 |                     | undefined,
235.3     210 |                   appliedColumnNames: metricColumn,
235.3     211 |                   columnsPropsObject: { colnames, coltypes },
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/controlPanel.tsx:222:22
235.3 TS2304: Cannot find name 't'.
235.3     220 |             config: {
235.3     221 |               type: 'CheckboxControl',
235.3   > 222 |               label: t('Circle radar shape'),
235.3         |                      ^
235.3     223 |               renderTrigger: true,
235.3     224 |               default: isCircle,
235.3     225 |               description: t(
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/controlPanel.tsx:225:28
235.3 TS2304: Cannot find name 't'.
235.3     223 |               renderTrigger: true,
235.3     224 |               default: isCircle,
235.3   > 225 |               description: t(
235.3         |                            ^
235.3     226 |                 "Radar render type, whether to display 'circle' shape.",
235.3     227 |               ),
235.3     228 |             },
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/transformProps.ts:158:7
235.3 TS2322: Type 'Set<unknown>' is not assignable to type 'Set<string>'.
235.3   Type 'unknown' is not assignable to type 'string'.
235.3     156 |       labelType,
235.3     157 |       getDenormalizedSeriesValue,
235.3   > 158 |       metricsWithCustomBounds,
235.3         |       ^^^^^^^^^^^^^^^^^^^^^^^
235.3     159 |       metricLabels,
235.3     160 |     });
235.3     161 |
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/transformProps.ts:342:7
235.3 TS2345: Argument of type 'Set<unknown>' is not assignable to parameter of type 'Set<string>'.
235.3     340 |       metricLabels,
235.3     341 |       getDenormalizedSeriesValue,
235.3   > 342 |       metricsWithCustomBounds,
235.3         |       ^^^^^^^^^^^^^^^^^^^^^^^
235.3     343 |     );
235.3     344 |
235.3     345 |   const echartOptions: EChartsCoreOption = {
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/types.ts:20:8
235.3 TS1141: String literal expected.
235.3     18 |  */
235.3     19 | import {
235.3   > 20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3        |        ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     21 |   QueryFormColumn,
235.3     22 |   QueryFormData,
235.3     23 |   QueryFormMetric,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/types.ts:20:118
235.3 TS2304: Cannot find name 'from'.
235.3     18 |  */
235.3     19 | import {
235.3   > 20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3        |                                                                                                                      ^^^^
235.3     21 |   QueryFormColumn,
235.3     22 |   QueryFormData,
235.3     23 |   QueryFormMetric,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/types.ts:21:3
235.3 TS2304: Cannot find name 'QueryFormColumn'.
235.3     19 | import {
235.3     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 21 |   QueryFormColumn,
235.3        |   ^^^^^^^^^^^^^^^
235.3     22 |   QueryFormData,
235.3     23 |   QueryFormMetric,
235.3     24 | } from '@superset-ui/core';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/types.ts:21:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     19 | import {
235.3     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 21 |   QueryFormColumn,
235.3        |   ^^^^^^^^^^^^^^^
235.3     22 |   QueryFormData,
235.3     23 |   QueryFormMetric,
235.3     24 | } from '@superset-ui/core';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/types.ts:21:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     19 | import {
235.3     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 21 |   QueryFormColumn,
235.3        |   ^^^^^^^^^^^^^^^^
235.3   > 22 |   QueryFormData,
235.3        | ^^^^^^^^^^^^^^^^
235.3     23 |   QueryFormMetric,
235.3     24 | } from '@superset-ui/core';
235.3     25 | import {
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/types.ts:21:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     19 | import {
235.3     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 21 |   QueryFormColumn,
235.3        |   ^^^^^^^^^^^^^^^^
235.3   > 22 |   QueryFormData,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 23 |   QueryFormMetric,
235.3        | ^^^^^^^^^^^^^^^^^^
235.3     24 | } from '@superset-ui/core';
235.3     25 | import {
235.3     26 |   BaseChartProps,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/types.ts:22:3
235.3 TS2304: Cannot find name 'QueryFormData'.
235.3     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3     21 |   QueryFormColumn,
235.3   > 22 |   QueryFormData,
235.3        |   ^^^^^^^^^^^^^
235.3     23 |   QueryFormMetric,
235.3     24 | } from '@superset-ui/core';
235.3     25 | import {
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/types.ts:23:3
235.3 TS2304: Cannot find name 'QueryFormMetric'.
235.3     21 |   QueryFormColumn,
235.3     22 |   QueryFormData,
235.3   > 23 |   QueryFormMetric,
235.3        |   ^^^^^^^^^^^^^^^
235.3     24 | } from '@superset-ui/core';
235.3     25 | import {
235.3     26 |   BaseChartProps,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/types.ts:24:3
235.3 TS2304: Cannot find name 'from'.
235.3     22 |   QueryFormData,
235.3     23 |   QueryFormMetric,
235.3   > 24 | } from '@superset-ui/core';
235.3        |   ^^^^
235.3     25 | import {
235.3     26 |   BaseChartProps,
235.3     27 |   BaseTransformedProps,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/types.ts:42:36
235.3 TS2304: Cannot find name 'QueryFormData'.
235.3     40 | >;
235.3     41 |
235.3   > 42 | export type EchartsRadarFormData = QueryFormData &
235.3        |                                    ^^^^^^^^^^^^^
235.3     43 |   LegendFormData & {
235.3     44 |     colorScheme?: string;
235.3     45 |     columnConfig?: RadarColumnConfig;
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/types.ts:49:14
235.3 TS2304: Cannot find name 'QueryFormColumn'.
235.3     47 |     currentValue?: string[] | null;
235.3     48 |     defaultValue?: string[] | null;
235.3   > 49 |     groupby: QueryFormColumn[];
235.3        |              ^^^^^^^^^^^^^^^
235.3     50 |     labelType: EchartsRadarLabelType;
235.3     51 |     labelPosition: LabelPositionEnum;
235.3     52 |     metrics: QueryFormMetric[];
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Radar/types.ts:52:14
235.3 TS2304: Cannot find name 'QueryFormMetric'.
235.3     50 |     labelType: EchartsRadarLabelType;
235.3     51 |     labelPosition: LabelPositionEnum;
235.3   > 52 |     metrics: QueryFormMetric[];
235.3        |              ^^^^^^^^^^^^^^^
235.3     53 |     showLabels: boolean;
235.3     54 |     isCircle: boolean;
235.3     55 |     numberFormat: string;
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sankey/types.ts:20:8
235.3 TS1141: String literal expected.
235.3     18 |  */
235.3     19 | import {
235.3   > 20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3        |        ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     21 |   QueryFormColumn,
235.3     22 |   QueryFormData,
235.3     23 |   QueryFormMetric,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sankey/types.ts:20:118
235.3 TS2304: Cannot find name 'from'.
235.3     18 |  */
235.3     19 | import {
235.3   > 20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3        |                                                                                                                      ^^^^
235.3     21 |   QueryFormColumn,
235.3     22 |   QueryFormData,
235.3     23 |   QueryFormMetric,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sankey/types.ts:21:3
235.3 TS2304: Cannot find name 'QueryFormColumn'.
235.3     19 | import {
235.3     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 21 |   QueryFormColumn,
235.3        |   ^^^^^^^^^^^^^^^
235.3     22 |   QueryFormData,
235.3     23 |   QueryFormMetric,
235.3     24 | } from '@superset-ui/core';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sankey/types.ts:21:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     19 | import {
235.3     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 21 |   QueryFormColumn,
235.3        |   ^^^^^^^^^^^^^^^
235.3     22 |   QueryFormData,
235.3     23 |   QueryFormMetric,
235.3     24 | } from '@superset-ui/core';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sankey/types.ts:21:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     19 | import {
235.3     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 21 |   QueryFormColumn,
235.3        |   ^^^^^^^^^^^^^^^^
235.3   > 22 |   QueryFormData,
235.3        | ^^^^^^^^^^^^^^^^
235.3     23 |   QueryFormMetric,
235.3     24 | } from '@superset-ui/core';
235.3     25 | import { BaseChartProps, BaseTransformedProps } from '../types';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sankey/types.ts:21:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     19 | import {
235.3     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 21 |   QueryFormColumn,
235.3        |   ^^^^^^^^^^^^^^^^
235.3   > 22 |   QueryFormData,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 23 |   QueryFormMetric,
235.3        | ^^^^^^^^^^^^^^^^^^
235.3     24 | } from '@superset-ui/core';
235.3     25 | import { BaseChartProps, BaseTransformedProps } from '../types';
235.3     26 |
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sankey/types.ts:22:3
235.3 TS2304: Cannot find name 'QueryFormData'.
235.3     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3     21 |   QueryFormColumn,
235.3   > 22 |   QueryFormData,
235.3        |   ^^^^^^^^^^^^^
235.3     23 |   QueryFormMetric,
235.3     24 | } from '@superset-ui/core';
235.3     25 | import { BaseChartProps, BaseTransformedProps } from '../types';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sankey/types.ts:23:3
235.3 TS2304: Cannot find name 'QueryFormMetric'.
235.3     21 |   QueryFormColumn,
235.3     22 |   QueryFormData,
235.3   > 23 |   QueryFormMetric,
235.3        |   ^^^^^^^^^^^^^^^
235.3     24 | } from '@superset-ui/core';
235.3     25 | import { BaseChartProps, BaseTransformedProps } from '../types';
235.3     26 |
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sankey/types.ts:24:3
235.3 TS2304: Cannot find name 'from'.
235.3     22 |   QueryFormData,
235.3     23 |   QueryFormMetric,
235.3   > 24 | } from '@superset-ui/core';
235.3        |   ^^^^
235.3     25 | import { BaseChartProps, BaseTransformedProps } from '../types';
235.3     26 |
235.3     27 | export type SankeyFormData = QueryFormData & {
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sankey/types.ts:27:30
235.3 TS2304: Cannot find name 'QueryFormData'.
235.3     25 | import { BaseChartProps, BaseTransformedProps } from '../types';
235.3     26 |
235.3   > 27 | export type SankeyFormData = QueryFormData & {
235.3        |                              ^^^^^^^^^^^^^
235.3     28 |   colorScheme: string;
235.3     29 |   metric: QueryFormMetric;
235.3     30 |   source: QueryFormColumn;
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sankey/types.ts:29:11
235.3 TS2304: Cannot find name 'QueryFormMetric'.
235.3     27 | export type SankeyFormData = QueryFormData & {
235.3     28 |   colorScheme: string;
235.3   > 29 |   metric: QueryFormMetric;
235.3        |           ^^^^^^^^^^^^^^^
235.3     30 |   source: QueryFormColumn;
235.3     31 |   target: QueryFormColumn;
235.3     32 | };
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sankey/types.ts:30:11
235.3 TS2304: Cannot find name 'QueryFormColumn'.
235.3     28 |   colorScheme: string;
235.3     29 |   metric: QueryFormMetric;
235.3   > 30 |   source: QueryFormColumn;
235.3        |           ^^^^^^^^^^^^^^^
235.3     31 |   target: QueryFormColumn;
235.3     32 | };
235.3     33 |
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sankey/types.ts:31:11
235.3 TS2304: Cannot find name 'QueryFormColumn'.
235.3     29 |   metric: QueryFormMetric;
235.3     30 |   source: QueryFormColumn;
235.3   > 31 |   target: QueryFormColumn;
235.3        |           ^^^^^^^^^^^^^^^
235.3     32 | };
235.3     33 |
235.3     34 | export interface SankeyChartProps extends BaseChartProps<SankeyFormData> {
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/buildQuery.ts:19:29
235.3 TS2300: Duplicate identifier 'QueryFormData'.
235.3     17 |  * under the License.
235.3     18 |  */
235.3   > 19 | import { buildQueryContext, QueryFormData } from '@superset-ui/core';
235.3        |                             ^^^^^^^^^^^^^
235.3     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3     21 |
235.3     22 | export default function buildQuery(formData: QueryFormData) {
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/buildQuery.ts:20:27
235.3 TS2300: Duplicate identifier 'QueryFormData'.
235.3     18 |  */
235.3     19 | import { buildQueryContext, QueryFormData } from '@superset-ui/core';
235.3   > 20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3        |                           ^^^^^^^^^^^^^
235.3     21 |
235.3     22 | export default function buildQuery(formData: QueryFormData) {
235.3     23 |   const { metric, sort_by_metric } = formData;
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/controlPanel.tsx:21:8
235.3 TS1141: String literal expected.
235.3     19 | import { t } from '@superset-ui/core';
235.3     20 | import {
235.3   > 21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3        |        ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     22 |   ControlPanelConfig,
235.3     23 |   ControlPanelsContainerProps,
235.3     24 |   ControlSubSectionHeader,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/controlPanel.tsx:21:118
235.3 TS2304: Cannot find name 'from'.
235.3     19 | import { t } from '@superset-ui/core';
235.3     20 | import {
235.3   > 21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3        |                                                                                                                      ^^^^
235.3     22 |   ControlPanelConfig,
235.3     23 |   ControlPanelsContainerProps,
235.3     24 |   ControlSubSectionHeader,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/controlPanel.tsx:22:3
235.3 TS2304: Cannot find name 'ControlPanelConfig'.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   ControlPanelConfig,
235.3        |   ^^^^^^^^^^^^^^^^^^
235.3     23 |   ControlPanelsContainerProps,
235.3     24 |   ControlSubSectionHeader,
235.3     25 |   D3_FORMAT_DOCS,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/controlPanel.tsx:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   ControlPanelConfig,
235.3        |   ^^^^^^^^^^^^^^^^^^
235.3     23 |   ControlPanelsContainerProps,
235.3     24 |   ControlSubSectionHeader,
235.3     25 |   D3_FORMAT_DOCS,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/controlPanel.tsx:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   ControlPanelConfig,
235.3        |   ^^^^^^^^^^^^^^^^^^^
235.3   > 23 |   ControlPanelsContainerProps,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     24 |   ControlSubSectionHeader,
235.3     25 |   D3_FORMAT_DOCS,
235.3     26 |   D3_NUMBER_FORMAT_DESCRIPTION_VALUES_TEXT,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/controlPanel.tsx:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   ControlPanelConfig,
235.3        |   ^^^^^^^^^^^^^^^^^^^
235.3   > 23 |   ControlPanelsContainerProps,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 24 |   ControlSubSectionHeader,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     25 |   D3_FORMAT_DOCS,
235.3     26 |   D3_NUMBER_FORMAT_DESCRIPTION_VALUES_TEXT,
235.3     27 |   D3_FORMAT_OPTIONS,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/controlPanel.tsx:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   ControlPanelConfig,
235.3        |   ^^^^^^^^^^^^^^^^^^^
235.3   > 23 |   ControlPanelsContainerProps,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 24 |   ControlSubSectionHeader,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 25 |   D3_FORMAT_DOCS,
235.3        | ^^^^^^^^^^^^^^^^^
235.3     26 |   D3_NUMBER_FORMAT_DESCRIPTION_VALUES_TEXT,
235.3     27 |   D3_FORMAT_OPTIONS,
235.3     28 |   D3_TIME_FORMAT_OPTIONS,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/controlPanel.tsx:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   ControlPanelConfig,
235.3        |   ^^^^^^^^^^^^^^^^^^^
235.3   > 23 |   ControlPanelsContainerProps,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 24 |   ControlSubSectionHeader,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 25 |   D3_FORMAT_DOCS,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 26 |   D3_NUMBER_FORMAT_DESCRIPTION_VALUES_TEXT,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     27 |   D3_FORMAT_OPTIONS,
235.3     28 |   D3_TIME_FORMAT_OPTIONS,
235.3     29 |   getStandardizedControls,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/controlPanel.tsx:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   ControlPanelConfig,
235.3        |   ^^^^^^^^^^^^^^^^^^^
235.3   > 23 |   ControlPanelsContainerProps,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 24 |   ControlSubSectionHeader,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 25 |   D3_FORMAT_DOCS,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 26 |   D3_NUMBER_FORMAT_DESCRIPTION_VALUES_TEXT,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 27 |   D3_FORMAT_OPTIONS,
235.3        | ^^^^^^^^^^^^^^^^^^^^
235.3     28 |   D3_TIME_FORMAT_OPTIONS,
235.3     29 |   getStandardizedControls,
235.3     30 | } from '@superset-ui/chart-controls';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/controlPanel.tsx:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   ControlPanelConfig,
235.3        |   ^^^^^^^^^^^^^^^^^^^
235.3   > 23 |   ControlPanelsContainerProps,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 24 |   ControlSubSectionHeader,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 25 |   D3_FORMAT_DOCS,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 26 |   D3_NUMBER_FORMAT_DESCRIPTION_VALUES_TEXT,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 27 |   D3_FORMAT_OPTIONS,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 28 |   D3_TIME_FORMAT_OPTIONS,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     29 |   getStandardizedControls,
235.3     30 | } from '@superset-ui/chart-controls';
235.3     31 | import { DEFAULT_FORM_DATA } from './types';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/controlPanel.tsx:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   ControlPanelConfig,
235.3        |   ^^^^^^^^^^^^^^^^^^^
235.3   > 23 |   ControlPanelsContainerProps,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 24 |   ControlSubSectionHeader,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 25 |   D3_FORMAT_DOCS,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 26 |   D3_NUMBER_FORMAT_DESCRIPTION_VALUES_TEXT,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 27 |   D3_FORMAT_OPTIONS,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 28 |   D3_TIME_FORMAT_OPTIONS,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 29 |   getStandardizedControls,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     30 | } from '@superset-ui/chart-controls';
235.3     31 | import { DEFAULT_FORM_DATA } from './types';
235.3     32 |
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/controlPanel.tsx:23:3
235.3 TS2304: Cannot find name 'ControlPanelsContainerProps'.
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3     22 |   ControlPanelConfig,
235.3   > 23 |   ControlPanelsContainerProps,
235.3        |   ^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     24 |   ControlSubSectionHeader,
235.3     25 |   D3_FORMAT_DOCS,
235.3     26 |   D3_NUMBER_FORMAT_DESCRIPTION_VALUES_TEXT,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/controlPanel.tsx:24:3
235.3 TS2304: Cannot find name 'ControlSubSectionHeader'.
235.3     22 |   ControlPanelConfig,
235.3     23 |   ControlPanelsContainerProps,
235.3   > 24 |   ControlSubSectionHeader,
235.3        |   ^^^^^^^^^^^^^^^^^^^^^^^
235.3     25 |   D3_FORMAT_DOCS,
235.3     26 |   D3_NUMBER_FORMAT_DESCRIPTION_VALUES_TEXT,
235.3     27 |   D3_FORMAT_OPTIONS,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/controlPanel.tsx:25:3
235.3 TS2304: Cannot find name 'D3_FORMAT_DOCS'.
235.3     23 |   ControlPanelsContainerProps,
235.3     24 |   ControlSubSectionHeader,
235.3   > 25 |   D3_FORMAT_DOCS,
235.3        |   ^^^^^^^^^^^^^^
235.3     26 |   D3_NUMBER_FORMAT_DESCRIPTION_VALUES_TEXT,
235.3     27 |   D3_FORMAT_OPTIONS,
235.3     28 |   D3_TIME_FORMAT_OPTIONS,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/controlPanel.tsx:26:3
235.3 TS2304: Cannot find name 'D3_NUMBER_FORMAT_DESCRIPTION_VALUES_TEXT'.
235.3     24 |   ControlSubSectionHeader,
235.3     25 |   D3_FORMAT_DOCS,
235.3   > 26 |   D3_NUMBER_FORMAT_DESCRIPTION_VALUES_TEXT,
235.3        |   ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     27 |   D3_FORMAT_OPTIONS,
235.3     28 |   D3_TIME_FORMAT_OPTIONS,
235.3     29 |   getStandardizedControls,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/controlPanel.tsx:27:3
235.3 TS2304: Cannot find name 'D3_FORMAT_OPTIONS'.
235.3     25 |   D3_FORMAT_DOCS,
235.3     26 |   D3_NUMBER_FORMAT_DESCRIPTION_VALUES_TEXT,
235.3   > 27 |   D3_FORMAT_OPTIONS,
235.3        |   ^^^^^^^^^^^^^^^^^
235.3     28 |   D3_TIME_FORMAT_OPTIONS,
235.3     29 |   getStandardizedControls,
235.3     30 | } from '@superset-ui/chart-controls';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/controlPanel.tsx:28:3
235.3 TS2304: Cannot find name 'D3_TIME_FORMAT_OPTIONS'.
235.3     26 |   D3_NUMBER_FORMAT_DESCRIPTION_VALUES_TEXT,
235.3     27 |   D3_FORMAT_OPTIONS,
235.3   > 28 |   D3_TIME_FORMAT_OPTIONS,
235.3        |   ^^^^^^^^^^^^^^^^^^^^^^
235.3     29 |   getStandardizedControls,
235.3     30 | } from '@superset-ui/chart-controls';
235.3     31 | import { DEFAULT_FORM_DATA } from './types';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/controlPanel.tsx:29:3
235.3 TS2304: Cannot find name 'getStandardizedControls'.
235.3     27 |   D3_FORMAT_OPTIONS,
235.3     28 |   D3_TIME_FORMAT_OPTIONS,
235.3   > 29 |   getStandardizedControls,
235.3        |   ^^^^^^^^^^^^^^^^^^^^^^^
235.3     30 | } from '@superset-ui/chart-controls';
235.3     31 | import { DEFAULT_FORM_DATA } from './types';
235.3     32 |
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/controlPanel.tsx:30:3
235.3 TS2304: Cannot find name 'from'.
235.3     28 |   D3_TIME_FORMAT_OPTIONS,
235.3     29 |   getStandardizedControls,
235.3   > 30 | } from '@superset-ui/chart-controls';
235.3        |   ^^^^
235.3     31 | import { DEFAULT_FORM_DATA } from './types';
235.3     32 |
235.3     33 | const { labelType, numberFormat, showLabels } = DEFAULT_FORM_DATA;
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/controlPanel.tsx:35:15
235.3 TS2304: Cannot find name 'ControlPanelConfig'.
235.3     33 | const { labelType, numberFormat, showLabels } = DEFAULT_FORM_DATA;
235.3     34 |
235.3   > 35 | const config: ControlPanelConfig = {
235.3        |               ^^^^^^^^^^^^^^^^^^
235.3     36 |   controlPanelSections: [
235.3     37 |     {
235.3     38 |       label: t('Query'),
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/controlPanel.tsx:55:11
235.3 TS2304: Cannot find name 'ControlSubSectionHeader'.
235.3     53 |         ['color_scheme'],
235.3     54 |         ['linear_color_scheme'],
235.3   > 55 |         [<ControlSubSectionHeader>{t('Labels')}</ControlSubSectionHeader>],
235.3        |           ^^^^^^^^^^^^^^^^^^^^^^^
235.3     56 |         [
235.3     57 |           {
235.3     58 |             name: 'show_labels',
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/controlPanel.tsx:55:50
235.3 TS2304: Cannot find name 'ControlSubSectionHeader'.
235.3     53 |         ['color_scheme'],
235.3     54 |         ['linear_color_scheme'],
235.3   > 55 |         [<ControlSubSectionHeader>{t('Labels')}</ControlSubSectionHeader>],
235.3        |                                                  ^^^^^^^^^^^^^^^^^^^^^^^
235.3     56 |         [
235.3     57 |           {
235.3     58 |             name: 'show_labels',
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/controlPanel.tsx:121:24
235.3 TS2304: Cannot find name 'D3_FORMAT_OPTIONS'.
235.3     119 |               renderTrigger: true,
235.3     120 |               default: numberFormat,
235.3   > 121 |               choices: D3_FORMAT_OPTIONS,
235.3         |                        ^^^^^^^^^^^^^^^^^
235.3     122 |               description: `${D3_FORMAT_DOCS} ${D3_NUMBER_FORMAT_DESCRIPTION_VALUES_TEXT}`,
235.3     123 |             },
235.3     124 |           },
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/controlPanel.tsx:122:31
235.3 TS2304: Cannot find name 'D3_FORMAT_DOCS'.
235.3     120 |               default: numberFormat,
235.3     121 |               choices: D3_FORMAT_OPTIONS,
235.3   > 122 |               description: `${D3_FORMAT_DOCS} ${D3_NUMBER_FORMAT_DESCRIPTION_VALUES_TEXT}`,
235.3         |                               ^^^^^^^^^^^^^^
235.3     123 |             },
235.3     124 |           },
235.3     125 |         ],
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/controlPanel.tsx:122:49
235.3 TS2304: Cannot find name 'D3_NUMBER_FORMAT_DESCRIPTION_VALUES_TEXT'.
235.3     120 |               default: numberFormat,
235.3     121 |               choices: D3_FORMAT_OPTIONS,
235.3   > 122 |               description: `${D3_FORMAT_DOCS} ${D3_NUMBER_FORMAT_DESCRIPTION_VALUES_TEXT}`,
235.3         |                                                 ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     123 |             },
235.3     124 |           },
235.3     125 |         ],
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/controlPanel.tsx:135:24
235.3 TS2304: Cannot find name 'D3_TIME_FORMAT_OPTIONS'.
235.3     133 |               label: t('Date format'),
235.3     134 |               renderTrigger: true,
235.3   > 135 |               choices: D3_TIME_FORMAT_OPTIONS,
235.3         |                        ^^^^^^^^^^^^^^^^^^^^^^
235.3     136 |               default: 'smart_date',
235.3     137 |               description: D3_FORMAT_DOCS,
235.3     138 |             },
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/controlPanel.tsx:137:28
235.3 TS2304: Cannot find name 'D3_FORMAT_DOCS'.
235.3     135 |               choices: D3_TIME_FORMAT_OPTIONS,
235.3     136 |               default: 'smart_date',
235.3   > 137 |               description: D3_FORMAT_DOCS,
235.3         |                            ^^^^^^^^^^^^^^
235.3     138 |             },
235.3     139 |           },
235.3     140 |         ],
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/controlPanel.tsx:164:34
235.3 TS2304: Cannot find name 'ControlPanelsContainerProps'.
235.3     162 |         'When only a primary metric is provided, a categorical color scale is used.',
235.3     163 |       ),
235.3   > 164 |       visibility: ({ controls }: ControlPanelsContainerProps) =>
235.3         |                                  ^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     165 |         Boolean(
235.3     166 |           !controls?.secondary_metric?.value ||
235.3     167 |             controls?.secondary_metric?.value === controls?.metric.value,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/controlPanel.tsx:174:34
235.3 TS2304: Cannot find name 'ControlPanelsContainerProps'.
235.3     172 |         'When a secondary metric is provided, a linear color scale is used.',
235.3     173 |       ),
235.3   > 174 |       visibility: ({ controls }: ControlPanelsContainerProps) =>
235.3         |                                  ^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     175 |         Boolean(
235.3     176 |           controls?.secondary_metric?.value &&
235.3     177 |             controls?.secondary_metric?.value !== controls?.metric.value,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/controlPanel.tsx:188:14
235.3 TS2304: Cannot find name 'getStandardizedControls'.
235.3     186 |   formDataOverrides: formData => ({
235.3     187 |     ...formData,
235.3   > 188 |     groupby: getStandardizedControls().popAllColumns(),
235.3         |              ^^^^^^^^^^^^^^^^^^^^^^^
235.3     189 |     metric: getStandardizedControls().shiftMetric(),
235.3     190 |     secondary_metric: getStandardizedControls().shiftMetric(),
235.3     191 |   }),
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/controlPanel.tsx:189:13
235.3 TS2304: Cannot find name 'getStandardizedControls'.
235.3     187 |     ...formData,
235.3     188 |     groupby: getStandardizedControls().popAllColumns(),
235.3   > 189 |     metric: getStandardizedControls().shiftMetric(),
235.3         |             ^^^^^^^^^^^^^^^^^^^^^^^
235.3     190 |     secondary_metric: getStandardizedControls().shiftMetric(),
235.3     191 |   }),
235.3     192 | };
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/controlPanel.tsx:190:23
235.3 TS2304: Cannot find name 'getStandardizedControls'.
235.3     188 |     groupby: getStandardizedControls().popAllColumns(),
235.3     189 |     metric: getStandardizedControls().shiftMetric(),
235.3   > 190 |     secondary_metric: getStandardizedControls().shiftMetric(),
235.3         |                       ^^^^^^^^^^^^^^^^^^^^^^^
235.3     191 |   }),
235.3     192 | };
235.3     193 |
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/transformProps.ts:163:5
235.3 TS2339: Property 'height' does not exist on type 'EchartsSunburstChartProps'.
235.3     161 |   const {
235.3     162 |     formData,
235.3   > 163 |     height,
235.3         |     ^^^^^^
235.3     164 |     hooks,
235.3     165 |     filterState,
235.3     166 |     queriesData,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/transformProps.ts:164:5
235.3 TS2339: Property 'hooks' does not exist on type 'EchartsSunburstChartProps'.
235.3     162 |     formData,
235.3     163 |     height,
235.3   > 164 |     hooks,
235.3         |     ^^^^^
235.3     165 |     filterState,
235.3     166 |     queriesData,
235.3     167 |     width,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/transformProps.ts:165:5
235.3 TS2339: Property 'filterState' does not exist on type 'EchartsSunburstChartProps'.
235.3     163 |     height,
235.3     164 |     hooks,
235.3   > 165 |     filterState,
235.3         |     ^^^^^^^^^^^
235.3     166 |     queriesData,
235.3     167 |     width,
235.3     168 |     theme,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/transformProps.ts:167:5
235.3 TS2339: Property 'width' does not exist on type 'EchartsSunburstChartProps'.
235.3     165 |     filterState,
235.3     166 |     queriesData,
235.3   > 167 |     width,
235.3         |     ^^^^^
235.3     168 |     theme,
235.3     169 |     inContextMenu,
235.3     170 |     emitCrossFilters,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/transformProps.ts:168:5
235.3 TS2339: Property 'theme' does not exist on type 'EchartsSunburstChartProps'.
235.3     166 |     queriesData,
235.3     167 |     width,
235.3   > 168 |     theme,
235.3         |     ^^^^^
235.3     169 |     inContextMenu,
235.3     170 |     emitCrossFilters,
235.3     171 |     datasource,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/transformProps.ts:169:5
235.3 TS2339: Property 'inContextMenu' does not exist on type 'EchartsSunburstChartProps'.
235.3     167 |     width,
235.3     168 |     theme,
235.3   > 169 |     inContextMenu,
235.3         |     ^^^^^^^^^^^^^
235.3     170 |     emitCrossFilters,
235.3     171 |     datasource,
235.3     172 |   } = chartProps;
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/transformProps.ts:170:5
235.3 TS2339: Property 'emitCrossFilters' does not exist on type 'EchartsSunburstChartProps'.
235.3     168 |     theme,
235.3     169 |     inContextMenu,
235.3   > 170 |     emitCrossFilters,
235.3         |     ^^^^^^^^^^^^^^^^
235.3     171 |     datasource,
235.3     172 |   } = chartProps;
235.3     173 |   const { data = [] } = queriesData[0];
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/transformProps.ts:171:5
235.3 TS2339: Property 'datasource' does not exist on type 'EchartsSunburstChartProps'.
235.3     169 |     inContextMenu,
235.3     170 |     emitCrossFilters,
235.3   > 171 |     datasource,
235.3         |     ^^^^^^^^^^
235.3     172 |   } = chartProps;
235.3     173 |   const { data = [] } = queriesData[0];
235.3     174 |   const coltypeMapping = getColtypesMapping(queriesData[0]);
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/types.ts:21:8
235.3 TS1141: String literal expected.
235.3     19 |
235.3     20 | import {
235.3   > 21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3        |        ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     22 |   ChartDataResponseResult,
235.3     23 |   ChartProps,
235.3     24 |   DataRecordValue,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/types.ts:21:118
235.3 TS2304: Cannot find name 'from'.
235.3     19 |
235.3     20 | import {
235.3   > 21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3        |                                                                                                                      ^^^^
235.3     22 |   ChartDataResponseResult,
235.3     23 |   ChartProps,
235.3     24 |   DataRecordValue,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/types.ts:22:3
235.3 TS2304: Cannot find name 'ChartDataResponseResult'.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   ChartDataResponseResult,
235.3        |   ^^^^^^^^^^^^^^^^^^^^^^^
235.3     23 |   ChartProps,
235.3     24 |   DataRecordValue,
235.3     25 |   QueryFormColumn,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/types.ts:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   ChartDataResponseResult,
235.3        |   ^^^^^^^^^^^^^^^^^^^^^^^
235.3     23 |   ChartProps,
235.3     24 |   DataRecordValue,
235.3     25 |   QueryFormColumn,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/types.ts:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   ChartDataResponseResult,
235.3        |   ^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 23 |   ChartProps,
235.3        | ^^^^^^^^^^^^^
235.3     24 |   DataRecordValue,
235.3     25 |   QueryFormColumn,
235.3     26 |   QueryFormData,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/types.ts:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   ChartDataResponseResult,
235.3        |   ^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 23 |   ChartProps,
235.3        | ^^^^^^^^^^^^^
235.3   > 24 |   DataRecordValue,
235.3        | ^^^^^^^^^^^^^^^^^^
235.3     25 |   QueryFormColumn,
235.3     26 |   QueryFormData,
235.3     27 |   QueryFormMetric,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/types.ts:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   ChartDataResponseResult,
235.3        |   ^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 23 |   ChartProps,
235.3        | ^^^^^^^^^^^^^
235.3   > 24 |   DataRecordValue,
235.3        | ^^^^^^^^^^^^^
235.3   > 25 |   QueryFormColumn,
235.3        | ^^^^^^^^^^^^^^^^^^
235.3     26 |   QueryFormData,
235.3     27 |   QueryFormMetric,
235.3     28 | } from '@superset-ui/core';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/types.ts:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   ChartDataResponseResult,
235.3        |   ^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 23 |   ChartProps,
235.3        | ^^^^^^^^^^^^^
235.3   > 24 |   DataRecordValue,
235.3        | ^^^^^^^^^^^^^
235.3   > 25 |   QueryFormColumn,
235.3        | ^^^^^^^^^^^^^
235.3   > 26 |   QueryFormData,
235.3        | ^^^^^^^^^^^^^^^^
235.3     27 |   QueryFormMetric,
235.3     28 | } from '@superset-ui/core';
235.3     29 | import type { SunburstSeriesNodeItemOption } from 'echarts/types/src/chart/sunburst/SunburstSeries';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/types.ts:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   ChartDataResponseResult,
235.3        |   ^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 23 |   ChartProps,
235.3        | ^^^^^^^^^^^^^
235.3   > 24 |   DataRecordValue,
235.3        | ^^^^^^^^^^^^^
235.3   > 25 |   QueryFormColumn,
235.3        | ^^^^^^^^^^^^^
235.3   > 26 |   QueryFormData,
235.3        | ^^^^^^^^^^^^^
235.3   > 27 |   QueryFormMetric,
235.3        | ^^^^^^^^^^^^^^^^^^
235.3     28 | } from '@superset-ui/core';
235.3     29 | import type { SunburstSeriesNodeItemOption } from 'echarts/types/src/chart/sunburst/SunburstSeries';
235.3     30 | import {
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/types.ts:23:3
235.3 TS2304: Cannot find name 'ChartProps'.
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3     22 |   ChartDataResponseResult,
235.3   > 23 |   ChartProps,
235.3        |   ^^^^^^^^^^
235.3     24 |   DataRecordValue,
235.3     25 |   QueryFormColumn,
235.3     26 |   QueryFormData,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/types.ts:24:3
235.3 TS2304: Cannot find name 'DataRecordValue'.
235.3     22 |   ChartDataResponseResult,
235.3     23 |   ChartProps,
235.3   > 24 |   DataRecordValue,
235.3        |   ^^^^^^^^^^^^^^^
235.3     25 |   QueryFormColumn,
235.3     26 |   QueryFormData,
235.3     27 |   QueryFormMetric,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/types.ts:25:3
235.3 TS2304: Cannot find name 'QueryFormColumn'.
235.3     23 |   ChartProps,
235.3     24 |   DataRecordValue,
235.3   > 25 |   QueryFormColumn,
235.3        |   ^^^^^^^^^^^^^^^
235.3     26 |   QueryFormData,
235.3     27 |   QueryFormMetric,
235.3     28 | } from '@superset-ui/core';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/types.ts:26:3
235.3 TS2304: Cannot find name 'QueryFormData'.
235.3     24 |   DataRecordValue,
235.3     25 |   QueryFormColumn,
235.3   > 26 |   QueryFormData,
235.3        |   ^^^^^^^^^^^^^
235.3     27 |   QueryFormMetric,
235.3     28 | } from '@superset-ui/core';
235.3     29 | import type { SunburstSeriesNodeItemOption } from 'echarts/types/src/chart/sunburst/SunburstSeries';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/types.ts:27:3
235.3 TS2304: Cannot find name 'QueryFormMetric'.
235.3     25 |   QueryFormColumn,
235.3     26 |   QueryFormData,
235.3   > 27 |   QueryFormMetric,
235.3        |   ^^^^^^^^^^^^^^^
235.3     28 | } from '@superset-ui/core';
235.3     29 | import type { SunburstSeriesNodeItemOption } from 'echarts/types/src/chart/sunburst/SunburstSeries';
235.3     30 | import {
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/types.ts:28:3
235.3 TS2304: Cannot find name 'from'.
235.3     26 |   QueryFormData,
235.3     27 |   QueryFormMetric,
235.3   > 28 | } from '@superset-ui/core';
235.3        |   ^^^^
235.3     29 | import type { SunburstSeriesNodeItemOption } from 'echarts/types/src/chart/sunburst/SunburstSeries';
235.3     30 | import {
235.3     31 |   BaseTransformedProps,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/types.ts:36:39
235.3 TS2304: Cannot find name 'QueryFormData'.
235.3     34 | } from '../types';
235.3     35 |
235.3   > 36 | export type EchartsSunburstFormData = QueryFormData & {
235.3        |                                       ^^^^^^^^^^^^^
235.3     37 |   groupby: QueryFormColumn[];
235.3     38 |   metric: QueryFormMetric;
235.3     39 |   secondaryMetric?: QueryFormMetric;
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/types.ts:37:12
235.3 TS2304: Cannot find name 'QueryFormColumn'.
235.3     35 |
235.3     36 | export type EchartsSunburstFormData = QueryFormData & {
235.3   > 37 |   groupby: QueryFormColumn[];
235.3        |            ^^^^^^^^^^^^^^^
235.3     38 |   metric: QueryFormMetric;
235.3     39 |   secondaryMetric?: QueryFormMetric;
235.3     40 |   colorScheme?: string;
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/types.ts:38:11
235.3 TS2304: Cannot find name 'QueryFormMetric'.
235.3     36 | export type EchartsSunburstFormData = QueryFormData & {
235.3     37 |   groupby: QueryFormColumn[];
235.3   > 38 |   metric: QueryFormMetric;
235.3        |           ^^^^^^^^^^^^^^^
235.3     39 |   secondaryMetric?: QueryFormMetric;
235.3     40 |   colorScheme?: string;
235.3     41 |   linearColorScheme?: string;
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/types.ts:39:21
235.3 TS2304: Cannot find name 'QueryFormMetric'.
235.3     37 |   groupby: QueryFormColumn[];
235.3     38 |   metric: QueryFormMetric;
235.3   > 39 |   secondaryMetric?: QueryFormMetric;
235.3        |                     ^^^^^^^^^^^^^^^
235.3     40 |   colorScheme?: string;
235.3     41 |   linearColorScheme?: string;
235.3     42 | };
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/types.ts:59:11
235.3 TS2304: Cannot find name 'ChartProps'.
235.3     57 |
235.3     58 | export interface EchartsSunburstChartProps
235.3   > 59 |   extends ChartProps<EchartsSunburstFormData> {
235.3        |           ^^^^^^^^^^
235.3     60 |   formData: EchartsSunburstFormData;
235.3     61 |   queriesData: ChartDataResponseResult[];
235.3     62 | }
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/types.ts:61:16
235.3 TS2304: Cannot find name 'ChartDataResponseResult'.
235.3     59 |   extends ChartProps<EchartsSunburstFormData> {
235.3     60 |   formData: EchartsSunburstFormData;
235.3   > 61 |   queriesData: ChartDataResponseResult[];
235.3        |                ^^^^^^^^^^^^^^^^^^^^^^^
235.3     62 | }
235.3     63 |
235.3     64 | export type SunburstTransformedProps =
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Sunburst/types.ts:70:12
235.3 TS2304: Cannot find name 'DataRecordValue'.
235.3     68 |
235.3     69 | export type NodeItemOption = SunburstSeriesNodeItemOption & {
235.3   > 70 |   records: DataRecordValue[];
235.3        |            ^^^^^^^^^^^^^^^
235.3     71 |   secondaryValue: number;
235.3     72 | };
235.3     73 |
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/buildQuery.ts:2:8
235.3 TS1141: String literal expected.
235.3     1 | import {
235.3   > 2 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3       |        ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     3 |   buildQueryContext,
235.3     4 |   ensureIsArray,
235.3     5 |   getXAxisColumn,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/buildQuery.ts:2:118
235.3 TS2304: Cannot find name 'from'.
235.3     1 | import {
235.3   > 2 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3       |                                                                                                                      ^^^^
235.3     3 |   buildQueryContext,
235.3     4 |   ensureIsArray,
235.3     5 |   getXAxisColumn,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/buildQuery.ts:3:3
235.3 TS2304: Cannot find name 'buildQueryContext'.
235.3     1 | import {
235.3     2 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 3 |   buildQueryContext,
235.3       |   ^^^^^^^^^^^^^^^^^
235.3     4 |   ensureIsArray,
235.3     5 |   getXAxisColumn,
235.3     6 |   isXAxisSet,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/buildQuery.ts:3:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     1 | import {
235.3     2 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 3 |   buildQueryContext,
235.3       |   ^^^^^^^^^^^^^^^^^
235.3     4 |   ensureIsArray,
235.3     5 |   getXAxisColumn,
235.3     6 |   isXAxisSet,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/buildQuery.ts:3:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     1 | import {
235.3     2 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 3 |   buildQueryContext,
235.3       |   ^^^^^^^^^^^^^^^^^^
235.3   > 4 |   ensureIsArray,
235.3       | ^^^^^^^^^^^^^^^^
235.3     5 |   getXAxisColumn,
235.3     6 |   isXAxisSet,
235.3     7 |   normalizeOrderBy,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/buildQuery.ts:3:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     1 | import {
235.3     2 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 3 |   buildQueryContext,
235.3       |   ^^^^^^^^^^^^^^^^^^
235.3   > 4 |   ensureIsArray,
235.3       | ^^^^^^^^^^^^^^^^
235.3   > 5 |   getXAxisColumn,
235.3       | ^^^^^^^^^^^^^^^^^
235.3     6 |   isXAxisSet,
235.3     7 |   normalizeOrderBy,
235.3     8 |   PostProcessingPivot,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/buildQuery.ts:3:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     1 | import {
235.3     2 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 3 |   buildQueryContext,
235.3       |   ^^^^^^^^^^^^^^^^^^
235.3   > 4 |   ensureIsArray,
235.3       | ^^^^^^^^^^^^^^^^
235.3   > 5 |   getXAxisColumn,
235.3       | ^^^^^^^^^^^^^^^^
235.3   > 6 |   isXAxisSet,
235.3       | ^^^^^^^^^^^^^
235.3     7 |   normalizeOrderBy,
235.3     8 |   PostProcessingPivot,
235.3     9 |   QueryFormData,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/buildQuery.ts:3:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3      1 | import {
235.3      2 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   >  3 |   buildQueryContext,
235.3        |   ^^^^^^^^^^^^^^^^^^
235.3   >  4 |   ensureIsArray,
235.3        | ^^^^^^^^^^^^^^^^
235.3   >  5 |   getXAxisColumn,
235.3        | ^^^^^^^^^^^^^^^^
235.3   >  6 |   isXAxisSet,
235.3        | ^^^^^^^^^^^^^^^^
235.3   >  7 |   normalizeOrderBy,
235.3        | ^^^^^^^^^^^^^^^^^^^
235.3      8 |   PostProcessingPivot,
235.3      9 |   QueryFormData,
235.3     10 |   getMetricLabel,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/buildQuery.ts:3:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3      1 | import {
235.3      2 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   >  3 |   buildQueryContext,
235.3        |   ^^^^^^^^^^^^^^^^^^
235.3   >  4 |   ensureIsArray,
235.3        | ^^^^^^^^^^^^^^^^
235.3   >  5 |   getXAxisColumn,
235.3        | ^^^^^^^^^^^^^^^^
235.3   >  6 |   isXAxisSet,
235.3        | ^^^^^^^^^^^^^^^^
235.3   >  7 |   normalizeOrderBy,
235.3        | ^^^^^^^^^^^^^^^^
235.3   >  8 |   PostProcessingPivot,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^
235.3      9 |   QueryFormData,
235.3     10 |   getMetricLabel,
235.3     11 |   NumpyFunction,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/buildQuery.ts:3:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3      1 | import {
235.3      2 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   >  3 |   buildQueryContext,
235.3        |   ^^^^^^^^^^^^^^^^^^
235.3   >  4 |   ensureIsArray,
235.3        | ^^^^^^^^^^^^^^^^
235.3   >  5 |   getXAxisColumn,
235.3        | ^^^^^^^^^^^^^^^^
235.3   >  6 |   isXAxisSet,
235.3        | ^^^^^^^^^^^^^^^^
235.3   >  7 |   normalizeOrderBy,
235.3        | ^^^^^^^^^^^^^^^^
235.3   >  8 |   PostProcessingPivot,
235.3        | ^^^^^^^^^^^^^^^^
235.3   >  9 |   QueryFormData,
235.3        | ^^^^^^^^^^^^^^^^
235.3     10 |   getMetricLabel,
235.3     11 |   NumpyFunction,
235.3     12 | } from '@superset-ui/core';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/buildQuery.ts:3:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3      1 | import {
235.3      2 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   >  3 |   buildQueryContext,
235.3        |   ^^^^^^^^^^^^^^^^^^
235.3   >  4 |   ensureIsArray,
235.3        | ^^^^^^^^^^^^^^^^
235.3   >  5 |   getXAxisColumn,
235.3        | ^^^^^^^^^^^^^^^^
235.3   >  6 |   isXAxisSet,
235.3        | ^^^^^^^^^^^^^^^^
235.3   >  7 |   normalizeOrderBy,
235.3        | ^^^^^^^^^^^^^^^^
235.3   >  8 |   PostProcessingPivot,
235.3        | ^^^^^^^^^^^^^^^^
235.3   >  9 |   QueryFormData,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 10 |   getMetricLabel,
235.3        | ^^^^^^^^^^^^^^^^^
235.3     11 |   NumpyFunction,
235.3     12 | } from '@superset-ui/core';
235.3     13 | import { contributionOperator,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/buildQuery.ts:3:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3      1 | import {
235.3      2 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   >  3 |   buildQueryContext,
235.3        |   ^^^^^^^^^^^^^^^^^^
235.3   >  4 |   ensureIsArray,
235.3        | ^^^^^^^^^^^^^^^^
235.3   >  5 |   getXAxisColumn,
235.3        | ^^^^^^^^^^^^^^^^
235.3   >  6 |   isXAxisSet,
235.3        | ^^^^^^^^^^^^^^^^
235.3   >  7 |   normalizeOrderBy,
235.3        | ^^^^^^^^^^^^^^^^
235.3   >  8 |   PostProcessingPivot,
235.3        | ^^^^^^^^^^^^^^^^
235.3   >  9 |   QueryFormData,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 10 |   getMetricLabel,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 11 |   NumpyFunction,
235.3        | ^^^^^^^^^^^^^^^^
235.3     12 | } from '@superset-ui/core';
235.3     13 | import { contributionOperator,
235.3     14 |   extractExtraMetrics,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/buildQuery.ts:4:3
235.3 TS2304: Cannot find name 'ensureIsArray'.
235.3     2 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3     3 |   buildQueryContext,
235.3   > 4 |   ensureIsArray,
235.3       |   ^^^^^^^^^^^^^
235.3     5 |   getXAxisColumn,
235.3     6 |   isXAxisSet,
235.3     7 |   normalizeOrderBy,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/buildQuery.ts:5:3
235.3 TS2304: Cannot find name 'getXAxisColumn'.
235.3     3 |   buildQueryContext,
235.3     4 |   ensureIsArray,
235.3   > 5 |   getXAxisColumn,
235.3       |   ^^^^^^^^^^^^^^
235.3     6 |   isXAxisSet,
235.3     7 |   normalizeOrderBy,
235.3     8 |   PostProcessingPivot,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/buildQuery.ts:6:3
235.3 TS2304: Cannot find name 'isXAxisSet'.
235.3     4 |   ensureIsArray,
235.3     5 |   getXAxisColumn,
235.3   > 6 |   isXAxisSet,
235.3       |   ^^^^^^^^^^
235.3     7 |   normalizeOrderBy,
235.3     8 |   PostProcessingPivot,
235.3     9 |   QueryFormData,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/buildQuery.ts:7:3
235.3 TS2304: Cannot find name 'normalizeOrderBy'.
235.3      5 |   getXAxisColumn,
235.3      6 |   isXAxisSet,
235.3   >  7 |   normalizeOrderBy,
235.3        |   ^^^^^^^^^^^^^^^^
235.3      8 |   PostProcessingPivot,
235.3      9 |   QueryFormData,
235.3     10 |   getMetricLabel,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/buildQuery.ts:8:3
235.3 TS2304: Cannot find name 'PostProcessingPivot'.
235.3      6 |   isXAxisSet,
235.3      7 |   normalizeOrderBy,
235.3   >  8 |   PostProcessingPivot,
235.3        |   ^^^^^^^^^^^^^^^^^^^
235.3      9 |   QueryFormData,
235.3     10 |   getMetricLabel,
235.3     11 |   NumpyFunction,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/buildQuery.ts:9:3
235.3 TS2304: Cannot find name 'QueryFormData'.
235.3      7 |   normalizeOrderBy,
235.3      8 |   PostProcessingPivot,
235.3   >  9 |   QueryFormData,
235.3        |   ^^^^^^^^^^^^^
235.3     10 |   getMetricLabel,
235.3     11 |   NumpyFunction,
235.3     12 | } from '@superset-ui/core';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/buildQuery.ts:10:3
235.3 TS2304: Cannot find name 'getMetricLabel'.
235.3      8 |   PostProcessingPivot,
235.3      9 |   QueryFormData,
235.3   > 10 |   getMetricLabel,
235.3        |   ^^^^^^^^^^^^^^
235.3     11 |   NumpyFunction,
235.3     12 | } from '@superset-ui/core';
235.3     13 | import { contributionOperator,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/buildQuery.ts:11:3
235.3 TS2304: Cannot find name 'NumpyFunction'.
235.3      9 |   QueryFormData,
235.3     10 |   getMetricLabel,
235.3   > 11 |   NumpyFunction,
235.3        |   ^^^^^^^^^^^^^
235.3     12 | } from '@superset-ui/core';
235.3     13 | import { contributionOperator,
235.3     14 |   extractExtraMetrics,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/buildQuery.ts:12:3
235.3 TS2304: Cannot find name 'from'.
235.3     10 |   getMetricLabel,
235.3     11 |   NumpyFunction,
235.3   > 12 | } from '@superset-ui/core';
235.3        |   ^^^^
235.3     13 | import { contributionOperator,
235.3     14 |   extractExtraMetrics,
235.3     15 |   flattenOperator,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/buildQuery.ts:23:3
235.3 TS2305: Module '"@superset-ui/chart-controls"' has no exported member 'timeComparePivotOperatorimeCompareOperator'.
235.3     21 |   rollingWindowOperator,
235.3     22 |   sortOperator,
235.3   > 23 |   timeComparePivotOperatorimeCompareOperator,
235.3        |   ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     24 |  } from '@superset-ui/chart-controls';
235.3     25 | import { t } from '@superset-ui/core';
235.3     26 |
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/buildQuery.ts:27:46
235.3 TS2304: Cannot find name 'QueryFormData'.
235.3     25 | import { t } from '@superset-ui/core';
235.3     26 |
235.3   > 27 | export default function buildQuery(formData: QueryFormData) {
235.3        |                                              ^^^^^^^^^^^^^
235.3     28 |   const {
235.3     29 |     groupby,
235.3     30 |     extra_tooltip_field,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/buildQuery.ts:41:27
235.3 TS2304: Cannot find name 'getMetricLabel'.
235.3     39 |   if (customUnitMetric) {
235.3     40 |     try {
235.3   > 41 |       customMetricLabel = getMetricLabel(customUnitMetric);
235.3        |                           ^^^^^^^^^^^^^^
235.3     42 |       console.log('✅ Custom SQL Unit Metric label:', customMetricLabel);
235.3     43 |       console.log('🧠 Raw custom_sql_unit_metric object:', customUnitMetric);
235.3     44 |     } catch (e) {
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/buildQuery.ts:49:10
235.3 TS2304: Cannot find name 'buildQueryContext'.
235.3     47 |   }
235.3     48 |
235.3   > 49 |   return buildQueryContext(formData, baseQueryObject => {
235.3        |          ^^^^^^^^^^^^^^^^^
235.3     50 |     const extra_metrics = extractExtraMetrics(formData);
235.3     51 |     const xAxisCols = isXAxisSet(formData)
235.3     52 |       ? ensureIsArray(getXAxisColumn(formData))
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/buildQuery.ts:51:23
235.3 TS2304: Cannot find name 'isXAxisSet'.
235.3     49 |   return buildQueryContext(formData, baseQueryObject => {
235.3     50 |     const extra_metrics = extractExtraMetrics(formData);
235.3   > 51 |     const xAxisCols = isXAxisSet(formData)
235.3        |                       ^^^^^^^^^^
235.3     52 |       ? ensureIsArray(getXAxisColumn(formData))
235.3     53 |       : [];
235.3     54 |     const extraFields = ensureIsArray(extra_tooltip_field);
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/buildQuery.ts:52:9
235.3 TS2304: Cannot find name 'ensureIsArray'.
235.3     50 |     const extra_metrics = extractExtraMetrics(formData);
235.3     51 |     const xAxisCols = isXAxisSet(formData)
235.3   > 52 |       ? ensureIsArray(getXAxisColumn(formData))
235.3        |         ^^^^^^^^^^^^^
235.3     53 |       : [];
235.3     54 |     const extraFields = ensureIsArray(extra_tooltip_field);
235.3     55 |
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/buildQuery.ts:52:23
235.3 TS2304: Cannot find name 'getXAxisColumn'.
235.3     50 |     const extra_metrics = extractExtraMetrics(formData);
235.3     51 |     const xAxisCols = isXAxisSet(formData)
235.3   > 52 |       ? ensureIsArray(getXAxisColumn(formData))
235.3        |                       ^^^^^^^^^^^^^^
235.3     53 |       : [];
235.3     54 |     const extraFields = ensureIsArray(extra_tooltip_field);
235.3     55 |
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/buildQuery.ts:54:25
235.3 TS2304: Cannot find name 'ensureIsArray'.
235.3     52 |       ? ensureIsArray(getXAxisColumn(formData))
235.3     53 |       : [];
235.3   > 54 |     const extraFields = ensureIsArray(extra_tooltip_field);
235.3        |                         ^^^^^^^^^^^^^
235.3     55 |
235.3     56 |     const cleanedExtraFields = extraFields.filter(
235.3     57 |       f => f && !groupby?.includes(f),
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/buildQuery.ts:62:47
235.3 TS2304: Cannot find name 'getMetricLabel'.
235.3     60 |     const cleanedMetrics = (baseQueryObject.metrics || []).filter(metric =>
235.3     61 |       !cleanedExtraFields.includes(
235.3   > 62 |         typeof metric === 'string' ? metric : getMetricLabel(metric),
235.3        |                                               ^^^^^^^^^^^^^^
235.3     63 |       ),
235.3     64 |     );
235.3     65 |
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/buildQuery.ts:67:9
235.3 TS2304: Cannot find name 'getMetricLabel'.
235.3     65 |
235.3     66 |     const unitMetricKey = custom_unit_metric
235.3   > 67 |       ? getMetricLabel(custom_unit_metric)
235.3        |         ^^^^^^^^^^^^^^
235.3     68 |       : null;
235.3     69 |
235.3     70 |     if (unitMetricKey) {
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/buildQuery.ts:80:10
235.3 TS2304: Cannot find name 'ensureIsArray'.
235.3     78 |     const columns = [
235.3     79 |       ...xAxisCols,
235.3   > 80 |       ...ensureIsArray(groupby),
235.3        |          ^^^^^^^^^^^^^
235.3     81 |       ...cleanedExtraFields,
235.3     82 |     ];
235.3     83 |
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/buildQuery.ts:88:35
235.3 TS2304: Cannot find name 'PostProcessingPivot'.
235.3     86 |       : [];
235.3     87 |
235.3   > 88 |     const pivotOperatorInRuntime: PostProcessingPivot = isTimeComparison(
235.3        |                                   ^^^^^^^^^^^^^^^^^^^
235.3     89 |       formData,
235.3     90 |       baseQueryObject,
235.3     91 |     )
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/buildQuery.ts:92:9
235.3 TS2304: Cannot find name 'timeComparePivotOperator'.
235.3     90 |       baseQueryObject,
235.3     91 |     )
235.3   > 92 |       ? timeComparePivotOperator(formData, baseQueryObject)
235.3        |         ^^^^^^^^^^^^^^^^^^^^^^^^
235.3     93 |       : {
235.3     94 |           operation: 'pivot',
235.3     95 |           options: {
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/buildQuery.ts:99:22
235.3 TS2304: Cannot find name 'ensureIsArray'.
235.3      97 |               .map(col => (typeof col === 'string' ? col : col.label))
235.3      98 |               .filter((val): val is string => Boolean(val)),
235.3   >  99 |             columns: ensureIsArray(groupby)
235.3         |                      ^^^^^^^^^^^^^
235.3     100 |               .map(col => (typeof col === 'string' ? col : col.label))
235.3     101 |               .filter((val): val is string => Boolean(val)),
235.3     102 |             drop_missing_columns: false,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/buildQuery.ts:111:69
235.3 TS2304: Cannot find name 'getMetricLabel'.
235.3     109 |               return Object.fromEntries(
235.3     110 |                 allFields.map(field => {
235.3   > 111 |                   const label = typeof field === 'string' ? field : getMetricLabel(field);
235.3         |                                                                     ^^^^^^^^^^^^^^
235.3     112 |                   const isTooltipField = cleanedExtraFields.includes(label);
235.3     113 |                   const operator: NumpyFunction = isTooltipField ? 'min' : 'mean';
235.3     114 |                   return [label, { operator }];
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/buildQuery.ts:113:35
235.3 TS2304: Cannot find name 'NumpyFunction'.
235.3     111 |                   const label = typeof field === 'string' ? field : getMetricLabel(field);
235.3     112 |                   const isTooltipField = cleanedExtraFields.includes(label);
235.3   > 113 |                   const operator: NumpyFunction = isTooltipField ? 'min' : 'mean';
235.3         |                                   ^^^^^^^^^^^^^
235.3     114 |                   return [label, { operator }];
235.3     115 |                 }),
235.3     116 |               );
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/buildQuery.ts:142:11
235.3 TS2304: Cannot find name 'isXAxisSet'.
235.3     140 |       custom_unit_metric,
235.3     141 |       series_columns: groupby,
235.3   > 142 |       ...(isXAxisSet(formData) ? {} : { is_timeseries: true }),
235.3         |           ^^^^^^^^^^
235.3     143 |       orderby: normalizeOrderBy(baseQueryObject).orderby,
235.3     144 |       time_offsets,
235.3     145 |       post_processing: [
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/buildQuery.ts:143:16
235.3 TS2304: Cannot find name 'normalizeOrderBy'.
235.3     141 |       series_columns: groupby,
235.3     142 |       ...(isXAxisSet(formData) ? {} : { is_timeseries: true }),
235.3   > 143 |       orderby: normalizeOrderBy(baseQueryObject).orderby,
235.3         |                ^^^^^^^^^^^^^^^^
235.3     144 |       time_offsets,
235.3     145 |       post_processing: [
235.3     146 |         pivotOperatorInRuntime,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/buildQuery.ts:148:9
235.3 TS2304: Cannot find name 'timeCompareOperator'.
235.3     146 |         pivotOperatorInRuntime,
235.3     147 |         rollingWindowOperator(formData, baseQueryObject),
235.3   > 148 |         timeCompareOperator(formData, baseQueryObject),
235.3         |         ^^^^^^^^^^^^^^^^^^^
235.3     149 |         resampleOperator(formData, baseQueryObject),
235.3     150 |         renameOperator(formData, baseQueryObject),
235.3     151 |         contributionOperator(formData, baseQueryObject, time_offsets),
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Regular/Line/controlPanel.tsx:21:8
235.3 TS1141: String literal expected.
235.3     19 | import { t } from '@superset-ui/core';
235.3     20 | import {
235.3   > 21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3        |        ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     22 |   ControlPanelConfig,
235.3     23 |   ControlPanelsContainerProps,
235.3     24 |   ControlSubSectionHeader,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Regular/Line/controlPanel.tsx:21:118
235.3 TS2304: Cannot find name 'from'.
235.3     19 | import { t } from '@superset-ui/core';
235.3     20 | import {
235.3   > 21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3        |                                                                                                                      ^^^^
235.3     22 |   ControlPanelConfig,
235.3     23 |   ControlPanelsContainerProps,
235.3     24 |   ControlSubSectionHeader,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Regular/Line/controlPanel.tsx:22:3
235.3 TS2304: Cannot find name 'ControlPanelConfig'.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   ControlPanelConfig,
235.3        |   ^^^^^^^^^^^^^^^^^^
235.3     23 |   ControlPanelsContainerProps,
235.3     24 |   ControlSubSectionHeader,
235.3     25 |   D3_TIME_FORMAT_DOCS,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Regular/Line/controlPanel.tsx:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   ControlPanelConfig,
235.3        |   ^^^^^^^^^^^^^^^^^^
235.3     23 |   ControlPanelsContainerProps,
235.3     24 |   ControlSubSectionHeader,
235.3     25 |   D3_TIME_FORMAT_DOCS,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Regular/Line/controlPanel.tsx:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   ControlPanelConfig,
235.3        |   ^^^^^^^^^^^^^^^^^^^
235.3   > 23 |   ControlPanelsContainerProps,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     24 |   ControlSubSectionHeader,
235.3     25 |   D3_TIME_FORMAT_DOCS,
235.3     26 |   getStandardizedControls,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Regular/Line/controlPanel.tsx:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   ControlPanelConfig,
235.3        |   ^^^^^^^^^^^^^^^^^^^
235.3   > 23 |   ControlPanelsContainerProps,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 24 |   ControlSubSectionHeader,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     25 |   D3_TIME_FORMAT_DOCS,
235.3     26 |   getStandardizedControls,
235.3     27 |   sections,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Regular/Line/controlPanel.tsx:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   ControlPanelConfig,
235.3        |   ^^^^^^^^^^^^^^^^^^^
235.3   > 23 |   ControlPanelsContainerProps,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 24 |   ControlSubSectionHeader,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 25 |   D3_TIME_FORMAT_DOCS,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^
235.3     26 |   getStandardizedControls,
235.3     27 |   sections,
235.3     28 |   sharedControls,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Regular/Line/controlPanel.tsx:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   ControlPanelConfig,
235.3        |   ^^^^^^^^^^^^^^^^^^^
235.3   > 23 |   ControlPanelsContainerProps,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 24 |   ControlSubSectionHeader,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 25 |   D3_TIME_FORMAT_DOCS,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 26 |   getStandardizedControls,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     27 |   sections,
235.3     28 |   sharedControls,
235.3     29 | } from '@superset-ui/chart-controls';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Regular/Line/controlPanel.tsx:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   ControlPanelConfig,
235.3        |   ^^^^^^^^^^^^^^^^^^^
235.3   > 23 |   ControlPanelsContainerProps,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 24 |   ControlSubSectionHeader,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 25 |   D3_TIME_FORMAT_DOCS,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 26 |   getStandardizedControls,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 27 |   sections,
235.3        | ^^^^^^^^^^^
235.3     28 |   sharedControls,
235.3     29 | } from '@superset-ui/chart-controls';
235.3     30 |
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Regular/Line/controlPanel.tsx:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   ControlPanelConfig,
235.3        |   ^^^^^^^^^^^^^^^^^^^
235.3   > 23 |   ControlPanelsContainerProps,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 24 |   ControlSubSectionHeader,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 25 |   D3_TIME_FORMAT_DOCS,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 26 |   getStandardizedControls,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 27 |   sections,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 28 |   sharedControls,
235.3        | ^^^^^^^^^^^^^^^^^
235.3     29 | } from '@superset-ui/chart-controls';
235.3     30 |
235.3     31 | import { EchartsTimeseriesSeriesType } from '../../types';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Regular/Line/controlPanel.tsx:23:3
235.3 TS2304: Cannot find name 'ControlPanelsContainerProps'.
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3     22 |   ControlPanelConfig,
235.3   > 23 |   ControlPanelsContainerProps,
235.3        |   ^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     24 |   ControlSubSectionHeader,
235.3     25 |   D3_TIME_FORMAT_DOCS,
235.3     26 |   getStandardizedControls,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Regular/Line/controlPanel.tsx:24:3
235.3 TS2304: Cannot find name 'ControlSubSectionHeader'.
235.3     22 |   ControlPanelConfig,
235.3     23 |   ControlPanelsContainerProps,
235.3   > 24 |   ControlSubSectionHeader,
235.3        |   ^^^^^^^^^^^^^^^^^^^^^^^
235.3     25 |   D3_TIME_FORMAT_DOCS,
235.3     26 |   getStandardizedControls,
235.3     27 |   sections,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Regular/Line/controlPanel.tsx:25:3
235.3 TS2304: Cannot find name 'D3_TIME_FORMAT_DOCS'.
235.3     23 |   ControlPanelsContainerProps,
235.3     24 |   ControlSubSectionHeader,
235.3   > 25 |   D3_TIME_FORMAT_DOCS,
235.3        |   ^^^^^^^^^^^^^^^^^^^
235.3     26 |   getStandardizedControls,
235.3     27 |   sections,
235.3     28 |   sharedControls,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Regular/Line/controlPanel.tsx:26:3
235.3 TS2304: Cannot find name 'getStandardizedControls'.
235.3     24 |   ControlSubSectionHeader,
235.3     25 |   D3_TIME_FORMAT_DOCS,
235.3   > 26 |   getStandardizedControls,
235.3        |   ^^^^^^^^^^^^^^^^^^^^^^^
235.3     27 |   sections,
235.3     28 |   sharedControls,
235.3     29 | } from '@superset-ui/chart-controls';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Regular/Line/controlPanel.tsx:27:3
235.3 TS2304: Cannot find name 'sections'.
235.3     25 |   D3_TIME_FORMAT_DOCS,
235.3     26 |   getStandardizedControls,
235.3   > 27 |   sections,
235.3        |   ^^^^^^^^
235.3     28 |   sharedControls,
235.3     29 | } from '@superset-ui/chart-controls';
235.3     30 |
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Regular/Line/controlPanel.tsx:28:3
235.3 TS2304: Cannot find name 'sharedControls'.
235.3     26 |   getStandardizedControls,
235.3     27 |   sections,
235.3   > 28 |   sharedControls,
235.3        |   ^^^^^^^^^^^^^^
235.3     29 | } from '@superset-ui/chart-controls';
235.3     30 |
235.3     31 | import { EchartsTimeseriesSeriesType } from '../../types';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Regular/Line/controlPanel.tsx:29:3
235.3 TS2304: Cannot find name 'from'.
235.3     27 |   sections,
235.3     28 |   sharedControls,
235.3   > 29 | } from '@superset-ui/chart-controls';
235.3        |   ^^^^
235.3     30 |
235.3     31 | import { EchartsTimeseriesSeriesType } from '../../types';
235.3     32 | import {
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Regular/Line/controlPanel.tsx:62:15
235.3 TS2304: Cannot find name 'ControlPanelConfig'.
235.3     60 | } = DEFAULT_FORM_DATA;
235.3     61 |
235.3   > 62 | const config: ControlPanelConfig = {
235.3        |               ^^^^^^^^^^^^^^^^^^
235.3     63 |   controlPanelSections: [
235.3     64 |     sections.echartsTimeSeriesQueryWithXAxisSort,
235.3     65 |     sections.advancedAnalyticsControls,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Regular/Line/controlPanel.tsx:64:5
235.3 TS2304: Cannot find name 'sections'.
235.3     62 | const config: ControlPanelConfig = {
235.3     63 |   controlPanelSections: [
235.3   > 64 |     sections.echartsTimeSeriesQueryWithXAxisSort,
235.3        |     ^^^^^^^^
235.3     65 |     sections.advancedAnalyticsControls,
235.3     66 |     sections.annotationsAndLayersControls,
235.3     67 |     sections.forecastIntervalControls,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Regular/Line/controlPanel.tsx:65:5
235.3 TS2304: Cannot find name 'sections'.
235.3     63 |   controlPanelSections: [
235.3     64 |     sections.echartsTimeSeriesQueryWithXAxisSort,
235.3   > 65 |     sections.advancedAnalyticsControls,
235.3        |     ^^^^^^^^
235.3     66 |     sections.annotationsAndLayersControls,
235.3     67 |     sections.forecastIntervalControls,
235.3     68 |     sections.titleControls,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Regular/Line/controlPanel.tsx:66:5
235.3 TS2304: Cannot find name 'sections'.
235.3     64 |     sections.echartsTimeSeriesQueryWithXAxisSort,
235.3     65 |     sections.advancedAnalyticsControls,
235.3   > 66 |     sections.annotationsAndLayersControls,
235.3        |     ^^^^^^^^
235.3     67 |     sections.forecastIntervalControls,
235.3     68 |     sections.titleControls,
235.3     69 |     {
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Regular/Line/controlPanel.tsx:67:5
235.3 TS2304: Cannot find name 'sections'.
235.3     65 |     sections.advancedAnalyticsControls,
235.3     66 |     sections.annotationsAndLayersControls,
235.3   > 67 |     sections.forecastIntervalControls,
235.3        |     ^^^^^^^^
235.3     68 |     sections.titleControls,
235.3     69 |     {
235.3     70 |       label: t('Chart Options'),
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Regular/Line/controlPanel.tsx:68:5
235.3 TS2304: Cannot find name 'sections'.
235.3     66 |     sections.annotationsAndLayersControls,
235.3     67 |     sections.forecastIntervalControls,
235.3   > 68 |     sections.titleControls,
235.3        |     ^^^^^^^^
235.3     69 |     {
235.3     70 |       label: t('Chart Options'),
235.3     71 |       expanded: true,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Regular/Line/controlPanel.tsx:116:18
235.3 TS2304: Cannot find name 'sharedControls'.
235.3     114 |             name: 'custom_unit_metric',
235.3     115 |             config: {
235.3   > 116 |               ...sharedControls.metric,
235.3         |                  ^^^^^^^^^^^^^^
235.3     117 |               label: t('Unit Metric'),
235.3     118 |               description: t(
235.3     119 |                 'Pick a column and aggregate function or write SQL to show result top-right of chart.'
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Regular/Line/controlPanel.tsx:140:42
235.3 TS2304: Cannot find name 'ControlPanelsContainerProps'.
235.3     138 |                 'Opacity of Area Chart. Also applies to confidence band.',
235.3     139 |               ),
235.3   > 140 |               visibility: ({ controls }: ControlPanelsContainerProps) =>
235.3         |                                          ^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     141 |                 Boolean(controls?.area?.value),
235.3     142 |             },
235.3     143 |           },
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Regular/Line/controlPanel.tsx:172:42
235.3 TS2304: Cannot find name 'ControlPanelsContainerProps'.
235.3     170 |                 'Size of marker. Also applies to forecast observations.',
235.3     171 |               ),
235.3   > 172 |               visibility: ({ controls }: ControlPanelsContainerProps) =>
235.3         |                                          ^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     173 |                 Boolean(controls?.markerEnabled?.value),
235.3     174 |             },
235.3     175 |           },
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Regular/Line/controlPanel.tsx:191:11
235.3 TS2304: Cannot find name 'ControlSubSectionHeader'.
235.3     189 |         [minorTicks],
235.3     190 |         ...legendSection,
235.3   > 191 |         [<ControlSubSectionHeader>{t('X Axis')}</ControlSubSectionHeader>],
235.3         |           ^^^^^^^^^^^^^^^^^^^^^^^
235.3     192 |         [
235.3     193 |           {
235.3     194 |             name: 'x_axis_time_format',
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Regular/Line/controlPanel.tsx:191:50
235.3 TS2304: Cannot find name 'ControlSubSectionHeader'.
235.3     189 |         [minorTicks],
235.3     190 |         ...legendSection,
235.3   > 191 |         [<ControlSubSectionHeader>{t('X Axis')}</ControlSubSectionHeader>],
235.3         |                                                  ^^^^^^^^^^^^^^^^^^^^^^^
235.3     192 |         [
235.3     193 |           {
235.3     194 |             name: 'x_axis_time_format',
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Regular/Line/controlPanel.tsx:196:18
235.3 TS2304: Cannot find name 'sharedControls'.
235.3     194 |             name: 'x_axis_time_format',
235.3     195 |             config: {
235.3   > 196 |               ...sharedControls.x_axis_time_format,
235.3         |                  ^^^^^^^^^^^^^^
235.3     197 |               default: 'smart_date',
235.3     198 |               description: `${D3_TIME_FORMAT_DOCS}. ${TIME_SERIES_DESCRIPTION_TEXT}`,
235.3     199 |             },
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Regular/Line/controlPanel.tsx:198:31
235.3 TS2304: Cannot find name 'D3_TIME_FORMAT_DOCS'.
235.3     196 |               ...sharedControls.x_axis_time_format,
235.3     197 |               default: 'smart_date',
235.3   > 198 |               description: `${D3_TIME_FORMAT_DOCS}. ${TIME_SERIES_DESCRIPTION_TEXT}`,
235.3         |                               ^^^^^^^^^^^^^^^^^^^
235.3     199 |             },
235.3     200 |           },
235.3     201 |         ],
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Regular/Line/controlPanel.tsx:205:11
235.3 TS2304: Cannot find name 'ControlSubSectionHeader'.
235.3     203 |         [xAxisLabelInterval],
235.3     204 |         ...richTooltipSection,
235.3   > 205 |         [<ControlSubSectionHeader>{t('Y Axis')}</ControlSubSectionHeader>],
235.3         |           ^^^^^^^^^^^^^^^^^^^^^^^
235.3     206 |         ['y_axis_format'],
235.3     207 |         ['currency_format'],
235.3     208 |         [
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Regular/Line/controlPanel.tsx:205:50
235.3 TS2304: Cannot find name 'ControlSubSectionHeader'.
235.3     203 |         [xAxisLabelInterval],
235.3     204 |         ...richTooltipSection,
235.3   > 205 |         [<ControlSubSectionHeader>{t('Y Axis')}</ControlSubSectionHeader>],
235.3         |                                                  ^^^^^^^^^^^^^^^^^^^^^^^
235.3     206 |         ['y_axis_format'],
235.3     207 |         ['currency_format'],
235.3     208 |         [
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Regular/Line/controlPanel.tsx:262:42
235.3 TS2304: Cannot find name 'ControlPanelsContainerProps'.
235.3     260 |                 "narrow the data's extent.",
235.3     261 |               ),
235.3   > 262 |               visibility: ({ controls }: ControlPanelsContainerProps) =>
235.3         |                                          ^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     263 |                 Boolean(controls?.truncateYAxis?.value),
235.3     264 |             },
235.3     265 |           },
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Regular/Line/controlPanel.tsx:277:14
235.3 TS2304: Cannot find name 'getStandardizedControls'.
235.3     275 |   formDataOverrides: formData => ({
235.3     276 |     ...formData,
235.3   > 277 |     metrics: getStandardizedControls().popAllMetrics(),
235.3         |              ^^^^^^^^^^^^^^^^^^^^^^^
235.3     278 |     groupby: getStandardizedControls().popAllColumns(),
235.3     279 |   }),
235.3     280 | };
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/Regular/Line/controlPanel.tsx:278:14
235.3 TS2304: Cannot find name 'getStandardizedControls'.
235.3     276 |     ...formData,
235.3     277 |     metrics: getStandardizedControls().popAllMetrics(),
235.3   > 278 |     groupby: getStandardizedControls().popAllColumns(),
235.3         |              ^^^^^^^^^^^^^^^^^^^^^^^
235.3     279 |   }),
235.3     280 | };
235.3     281 |
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformers.ts:28:3
235.3 TS2724: '"@superset-ui/core"' has no exported member named 'isTimeseriesAnnotationResult'. Did you mean 'isTimeseriesAnnotationLayer'?
235.3     26 |   FormulaAnnotationLayer,
235.3     27 |   IntervalAnnotationLayer,
235.3   > 28 |   isTimeseriesAnnotationResult,
235.3        |   ^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     29 |   LegendState,
235.3     30 |   SupersetTheme,
235.3     31 |   TimeseriesAnnotationLayer,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:22:8
235.3 TS1141: String literal expected.
235.3     20 | import { invert } from 'lodash';
235.3     21 | import {
235.3   > 22 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3        |        ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     23 |   AnnotationLayer,
235.3     24 |   AxisType,
235.3     25 |   buildCustomFormatters,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:22:118
235.3 TS2304: Cannot find name 'from'.
235.3     20 | import { invert } from 'lodash';
235.3     21 | import {
235.3   > 22 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3        |                                                                                                                      ^^^^
235.3     23 |   AnnotationLayer,
235.3     24 |   AxisType,
235.3     25 |   buildCustomFormatters,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:23:3
235.3 TS2304: Cannot find name 'AnnotationLayer'.
235.3     21 | import {
235.3     22 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 23 |   AnnotationLayer,
235.3        |   ^^^^^^^^^^^^^^^
235.3     24 |   AxisType,
235.3     25 |   buildCustomFormatters,
235.3     26 |   CategoricalColorNamespace,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:23:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     21 | import {
235.3     22 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 23 |   AnnotationLayer,
235.3        |   ^^^^^^^^^^^^^^^
235.3     24 |   AxisType,
235.3     25 |   buildCustomFormatters,
235.3     26 |   CategoricalColorNamespace,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:23:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     21 | import {
235.3     22 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 23 |   AnnotationLayer,
235.3        |   ^^^^^^^^^^^^^^^^
235.3   > 24 |   AxisType,
235.3        | ^^^^^^^^^^^
235.3     25 |   buildCustomFormatters,
235.3     26 |   CategoricalColorNamespace,
235.3     27 |   CurrencyFormatter,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:23:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     21 | import {
235.3     22 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 23 |   AnnotationLayer,
235.3        |   ^^^^^^^^^^^^^^^^
235.3   > 24 |   AxisType,
235.3        | ^^^^^^^^^^^
235.3   > 25 |   buildCustomFormatters,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^
235.3     26 |   CategoricalColorNamespace,
235.3     27 |   CurrencyFormatter,
235.3     28 |   ensureIsArray,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:23:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     21 | import {
235.3     22 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 23 |   AnnotationLayer,
235.3        |   ^^^^^^^^^^^^^^^^
235.3   > 24 |   AxisType,
235.3        | ^^^^^^^^^^^
235.3   > 25 |   buildCustomFormatters,
235.3        | ^^^^^^^^^^^
235.3   > 26 |   CategoricalColorNamespace,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     27 |   CurrencyFormatter,
235.3     28 |   ensureIsArray,
235.3     29 |   tooltipHtml,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:23:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     21 | import {
235.3     22 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 23 |   AnnotationLayer,
235.3        |   ^^^^^^^^^^^^^^^^
235.3   > 24 |   AxisType,
235.3        | ^^^^^^^^^^^
235.3   > 25 |   buildCustomFormatters,
235.3        | ^^^^^^^^^^^
235.3   > 26 |   CategoricalColorNamespace,
235.3        | ^^^^^^^^^^^
235.3   > 27 |   CurrencyFormatter,
235.3        | ^^^^^^^^^^^^^^^^^^^^
235.3     28 |   ensureIsArray,
235.3     29 |   tooltipHtml,
235.3     30 |   GenericDataType,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:23:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     21 | import {
235.3     22 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 23 |   AnnotationLayer,
235.3        |   ^^^^^^^^^^^^^^^^
235.3   > 24 |   AxisType,
235.3        | ^^^^^^^^^^^
235.3   > 25 |   buildCustomFormatters,
235.3        | ^^^^^^^^^^^
235.3   > 26 |   CategoricalColorNamespace,
235.3        | ^^^^^^^^^^^
235.3   > 27 |   CurrencyFormatter,
235.3        | ^^^^^^^^^^^
235.3   > 28 |   ensureIsArray,
235.3        | ^^^^^^^^^^^^^^^^
235.3     29 |   tooltipHtml,
235.3     30 |   GenericDataType,
235.3     31 |   getCustomFormatter,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:23:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     21 | import {
235.3     22 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 23 |   AnnotationLayer,
235.3        |   ^^^^^^^^^^^^^^^^
235.3   > 24 |   AxisType,
235.3        | ^^^^^^^^^^^
235.3   > 25 |   buildCustomFormatters,
235.3        | ^^^^^^^^^^^
235.3   > 26 |   CategoricalColorNamespace,
235.3        | ^^^^^^^^^^^
235.3   > 27 |   CurrencyFormatter,
235.3        | ^^^^^^^^^^^
235.3   > 28 |   ensureIsArray,
235.3        | ^^^^^^^^^^^
235.3   > 29 |   tooltipHtml,
235.3        | ^^^^^^^^^^^^^^
235.3     30 |   GenericDataType,
235.3     31 |   getCustomFormatter,
235.3     32 |   getMetricLabel,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:23:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     21 | import {
235.3     22 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 23 |   AnnotationLayer,
235.3        |   ^^^^^^^^^^^^^^^^
235.3   > 24 |   AxisType,
235.3        | ^^^^^^^^^^^
235.3   > 25 |   buildCustomFormatters,
235.3        | ^^^^^^^^^^^
235.3   > 26 |   CategoricalColorNamespace,
235.3        | ^^^^^^^^^^^
235.3   > 27 |   CurrencyFormatter,
235.3        | ^^^^^^^^^^^
235.3   > 28 |   ensureIsArray,
235.3        | ^^^^^^^^^^^
235.3   > 29 |   tooltipHtml,
235.3        | ^^^^^^^^^^^
235.3   > 30 |   GenericDataType,
235.3        | ^^^^^^^^^^^^^^^^^^
235.3     31 |   getCustomFormatter,
235.3     32 |   getMetricLabel,
235.3     33 |   getNumberFormatter,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:23:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     21 | import {
235.3     22 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 23 |   AnnotationLayer,
235.3        |   ^^^^^^^^^^^^^^^^
235.3   > 24 |   AxisType,
235.3        | ^^^^^^^^^^^
235.3   > 25 |   buildCustomFormatters,
235.3        | ^^^^^^^^^^^
235.3   > 26 |   CategoricalColorNamespace,
235.3        | ^^^^^^^^^^^
235.3   > 27 |   CurrencyFormatter,
235.3        | ^^^^^^^^^^^
235.3   > 28 |   ensureIsArray,
235.3        | ^^^^^^^^^^^
235.3   > 29 |   tooltipHtml,
235.3        | ^^^^^^^^^^^
235.3   > 30 |   GenericDataType,
235.3        | ^^^^^^^^^^^
235.3   > 31 |   getCustomFormatter,
235.3        | ^^^^^^^^^^^^^^^^^^^^^
235.3     32 |   getMetricLabel,
235.3     33 |   getNumberFormatter,
235.3     34 |   getXAxisLabel,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:23:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     21 | import {
235.3     22 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 23 |   AnnotationLayer,
235.3        |   ^^^^^^^^^^^^^^^^
235.3   > 24 |   AxisType,
235.3        | ^^^^^^^^^^^
235.3   > 25 |   buildCustomFormatters,
235.3        | ^^^^^^^^^^^
235.3   > 26 |   CategoricalColorNamespace,
235.3        | ^^^^^^^^^^^
235.3   > 27 |   CurrencyFormatter,
235.3        | ^^^^^^^^^^^
235.3   > 28 |   ensureIsArray,
235.3        | ^^^^^^^^^^^
235.3   > 29 |   tooltipHtml,
235.3        | ^^^^^^^^^^^
235.3   > 30 |   GenericDataType,
235.3        | ^^^^^^^^^^^
235.3   > 31 |   getCustomFormatter,
235.3        | ^^^^^^^^^^^
235.3   > 32 |   getMetricLabel,
235.3        | ^^^^^^^^^^^^^^^^^
235.3     33 |   getNumberFormatter,
235.3     34 |   getXAxisLabel,
235.3     35 |   isDefined,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:23:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     21 | import {
235.3     22 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 23 |   AnnotationLayer,
235.3        |   ^^^^^^^^^^^^^^^^
235.3   > 24 |   AxisType,
235.3        | ^^^^^^^^^^^
235.3   > 25 |   buildCustomFormatters,
235.3        | ^^^^^^^^^^^
235.3   > 26 |   CategoricalColorNamespace,
235.3        | ^^^^^^^^^^^
235.3   > 27 |   CurrencyFormatter,
235.3        | ^^^^^^^^^^^
235.3   > 28 |   ensureIsArray,
235.3        | ^^^^^^^^^^^
235.3   > 29 |   tooltipHtml,
235.3        | ^^^^^^^^^^^
235.3   > 30 |   GenericDataType,
235.3        | ^^^^^^^^^^^
235.3   > 31 |   getCustomFormatter,
235.3        | ^^^^^^^^^^^
235.3   > 32 |   getMetricLabel,
235.3        | ^^^^^^^^^^^
235.3   > 33 |   getNumberFormatter,
235.3        | ^^^^^^^^^^^^^^^^^^^^^
235.3     34 |   getXAxisLabel,
235.3     35 |   isDefined,
235.3     36 |   isEventAnnotationLayer,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:23:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     21 | import {
235.3     22 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 23 |   AnnotationLayer,
235.3        |   ^^^^^^^^^^^^^^^^
235.3   > 24 |   AxisType,
235.3        | ^^^^^^^^^^^
235.3   > 25 |   buildCustomFormatters,
235.3        | ^^^^^^^^^^^
235.3   > 26 |   CategoricalColorNamespace,
235.3        | ^^^^^^^^^^^
235.3   > 27 |   CurrencyFormatter,
235.3        | ^^^^^^^^^^^
235.3   > 28 |   ensureIsArray,
235.3        | ^^^^^^^^^^^
235.3   > 29 |   tooltipHtml,
235.3        | ^^^^^^^^^^^
235.3   > 30 |   GenericDataType,
235.3        | ^^^^^^^^^^^
235.3   > 31 |   getCustomFormatter,
235.3        | ^^^^^^^^^^^
235.3   > 32 |   getMetricLabel,
235.3        | ^^^^^^^^^^^
235.3   > 33 |   getNumberFormatter,
235.3        | ^^^^^^^^^^^
235.3   > 34 |   getXAxisLabel,
235.3        | ^^^^^^^^^^^^^^^^
235.3     35 |   isDefined,
235.3     36 |   isEventAnnotationLayer,
235.3     37 |   isFormulaAnnotationLayer,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:23:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     21 | import {
235.3     22 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 23 |   AnnotationLayer,
235.3        |   ^^^^^^^^^^^^^^^^
235.3   > 24 |   AxisType,
235.3        | ^^^^^^^^^^^
235.3   > 25 |   buildCustomFormatters,
235.3        | ^^^^^^^^^^^
235.3   > 26 |   CategoricalColorNamespace,
235.3        | ^^^^^^^^^^^
235.3   > 27 |   CurrencyFormatter,
235.3        | ^^^^^^^^^^^
235.3   > 28 |   ensureIsArray,
235.3        | ^^^^^^^^^^^
235.3   > 29 |   tooltipHtml,
235.3        | ^^^^^^^^^^^
235.3   > 30 |   GenericDataType,
235.3        | ^^^^^^^^^^^
235.3   > 31 |   getCustomFormatter,
235.3        | ^^^^^^^^^^^
235.3   > 32 |   getMetricLabel,
235.3        | ^^^^^^^^^^^
235.3   > 33 |   getNumberFormatter,
235.3        | ^^^^^^^^^^^
235.3   > 34 |   getXAxisLabel,
235.3        | ^^^^^^^^^^^
235.3   > 35 |   isDefined,
235.3        | ^^^^^^^^^^^^
235.3     36 |   isEventAnnotationLayer,
235.3     37 |   isFormulaAnnotationLayer,
235.3     38 |   isIntervalAnnotationLayer,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:23:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     21 | import {
235.3     22 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 23 |   AnnotationLayer,
235.3        |   ^^^^^^^^^^^^^^^^
235.3   > 24 |   AxisType,
235.3        | ^^^^^^^^^^^
235.3   > 25 |   buildCustomFormatters,
235.3        | ^^^^^^^^^^^
235.3   > 26 |   CategoricalColorNamespace,
235.3        | ^^^^^^^^^^^
235.3   > 27 |   CurrencyFormatter,
235.3        | ^^^^^^^^^^^
235.3   > 28 |   ensureIsArray,
235.3        | ^^^^^^^^^^^
235.3   > 29 |   tooltipHtml,
235.3        | ^^^^^^^^^^^
235.3   > 30 |   GenericDataType,
235.3        | ^^^^^^^^^^^
235.3   > 31 |   getCustomFormatter,
235.3        | ^^^^^^^^^^^
235.3   > 32 |   getMetricLabel,
235.3        | ^^^^^^^^^^^
235.3   > 33 |   getNumberFormatter,
235.3        | ^^^^^^^^^^^
235.3   > 34 |   getXAxisLabel,
235.3        | ^^^^^^^^^^^
235.3   > 35 |   isDefined,
235.3        | ^^^^^^^^^^^
235.3   > 36 |   isEventAnnotationLayer,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     37 |   isFormulaAnnotationLayer,
235.3     38 |   isIntervalAnnotationLayer,
235.3     39 |   isPhysicalColumn,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:23:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     21 | import {
235.3     22 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 23 |   AnnotationLayer,
235.3        |   ^^^^^^^^^^^^^^^^
235.3   > 24 |   AxisType,
235.3        | ^^^^^^^^^^^
235.3   > 25 |   buildCustomFormatters,
235.3        | ^^^^^^^^^^^
235.3   > 26 |   CategoricalColorNamespace,
235.3        | ^^^^^^^^^^^
235.3   > 27 |   CurrencyFormatter,
235.3        | ^^^^^^^^^^^
235.3   > 28 |   ensureIsArray,
235.3        | ^^^^^^^^^^^
235.3   > 29 |   tooltipHtml,
235.3        | ^^^^^^^^^^^
235.3   > 30 |   GenericDataType,
235.3        | ^^^^^^^^^^^
235.3   > 31 |   getCustomFormatter,
235.3        | ^^^^^^^^^^^
235.3   > 32 |   getMetricLabel,
235.3        | ^^^^^^^^^^^
235.3   > 33 |   getNumberFormatter,
235.3        | ^^^^^^^^^^^
235.3   > 34 |   getXAxisLabel,
235.3        | ^^^^^^^^^^^
235.3   > 35 |   isDefined,
235.3        | ^^^^^^^^^^^
235.3   > 36 |   isEventAnnotationLayer,
235.3        | ^^^^^^^^^^^
235.3   > 37 |   isFormulaAnnotationLayer,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     38 |   isIntervalAnnotationLayer,
235.3     39 |   isPhysicalColumn,
235.3     40 |   isTimeseriesAnnotationLayer,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:23:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     21 | import {
235.3     22 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 23 |   AnnotationLayer,
235.3        |   ^^^^^^^^^^^^^^^^
235.3   > 24 |   AxisType,
235.3        | ^^^^^^^^^^^
235.3   > 25 |   buildCustomFormatters,
235.3        | ^^^^^^^^^^^
235.3   > 26 |   CategoricalColorNamespace,
235.3        | ^^^^^^^^^^^
235.3   > 27 |   CurrencyFormatter,
235.3        | ^^^^^^^^^^^
235.3   > 28 |   ensureIsArray,
235.3        | ^^^^^^^^^^^
235.3   > 29 |   tooltipHtml,
235.3        | ^^^^^^^^^^^
235.3   > 30 |   GenericDataType,
235.3        | ^^^^^^^^^^^
235.3   > 31 |   getCustomFormatter,
235.3        | ^^^^^^^^^^^
235.3   > 32 |   getMetricLabel,
235.3        | ^^^^^^^^^^^
235.3   > 33 |   getNumberFormatter,
235.3        | ^^^^^^^^^^^
235.3   > 34 |   getXAxisLabel,
235.3        | ^^^^^^^^^^^
235.3   > 35 |   isDefined,
235.3        | ^^^^^^^^^^^
235.3   > 36 |   isEventAnnotationLayer,
235.3        | ^^^^^^^^^^^
235.3   > 37 |   isFormulaAnnotationLayer,
235.3        | ^^^^^^^^^^^
235.3   > 38 |   isIntervalAnnotationLayer,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     39 |   isPhysicalColumn,
235.3     40 |   isTimeseriesAnnotationLayer,
235.3     41 |   t,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:23:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     21 | import {
235.3     22 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 23 |   AnnotationLayer,
235.3        |   ^^^^^^^^^^^^^^^^
235.3   > 24 |   AxisType,
235.3        | ^^^^^^^^^^^
235.3   > 25 |   buildCustomFormatters,
235.3        | ^^^^^^^^^^^
235.3   > 26 |   CategoricalColorNamespace,
235.3        | ^^^^^^^^^^^
235.3   > 27 |   CurrencyFormatter,
235.3        | ^^^^^^^^^^^
235.3   > 28 |   ensureIsArray,
235.3        | ^^^^^^^^^^^
235.3   > 29 |   tooltipHtml,
235.3        | ^^^^^^^^^^^
235.3   > 30 |   GenericDataType,
235.3        | ^^^^^^^^^^^
235.3   > 31 |   getCustomFormatter,
235.3        | ^^^^^^^^^^^
235.3   > 32 |   getMetricLabel,
235.3        | ^^^^^^^^^^^
235.3   > 33 |   getNumberFormatter,
235.3        | ^^^^^^^^^^^
235.3   > 34 |   getXAxisLabel,
235.3        | ^^^^^^^^^^^
235.3   > 35 |   isDefined,
235.3        | ^^^^^^^^^^^
235.3   > 36 |   isEventAnnotationLayer,
235.3        | ^^^^^^^^^^^
235.3   > 37 |   isFormulaAnnotationLayer,
235.3        | ^^^^^^^^^^^
235.3   > 38 |   isIntervalAnnotationLayer,
235.3        | ^^^^^^^^^^^
235.3   > 39 |   isPhysicalColumn,
235.3        | ^^^^^^^^^^^^^^^^^^^
235.3     40 |   isTimeseriesAnnotationLayer,
235.3     41 |   t,
235.3     42 |   TimeseriesChartDataResponseResult,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:23:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     21 | import {
235.3     22 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 23 |   AnnotationLayer,
235.3        |   ^^^^^^^^^^^^^^^^
235.3   > 24 |   AxisType,
235.3        | ^^^^^^^^^^^
235.3   > 25 |   buildCustomFormatters,
235.3        | ^^^^^^^^^^^
235.3   > 26 |   CategoricalColorNamespace,
235.3        | ^^^^^^^^^^^
235.3   > 27 |   CurrencyFormatter,
235.3        | ^^^^^^^^^^^
235.3   > 28 |   ensureIsArray,
235.3        | ^^^^^^^^^^^
235.3   > 29 |   tooltipHtml,
235.3        | ^^^^^^^^^^^
235.3   > 30 |   GenericDataType,
235.3        | ^^^^^^^^^^^
235.3   > 31 |   getCustomFormatter,
235.3        | ^^^^^^^^^^^
235.3   > 32 |   getMetricLabel,
235.3        | ^^^^^^^^^^^
235.3   > 33 |   getNumberFormatter,
235.3        | ^^^^^^^^^^^
235.3   > 34 |   getXAxisLabel,
235.3        | ^^^^^^^^^^^
235.3   > 35 |   isDefined,
235.3        | ^^^^^^^^^^^
235.3   > 36 |   isEventAnnotationLayer,
235.3        | ^^^^^^^^^^^
235.3   > 37 |   isFormulaAnnotationLayer,
235.3        | ^^^^^^^^^^^
235.3   > 38 |   isIntervalAnnotationLayer,
235.3        | ^^^^^^^^^^^
235.3   > 39 |   isPhysicalColumn,
235.3        | ^^^^^^^^^^^
235.3   > 40 |   isTimeseriesAnnotationLayer,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     41 |   t,
235.3     42 |   TimeseriesChartDataResponseResult,
235.3     43 |   NumberFormats,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:23:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     21 | import {
235.3     22 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 23 |   AnnotationLayer,
235.3        |   ^^^^^^^^^^^^^^^^
235.3   > 24 |   AxisType,
235.3        | ^^^^^^^^^^^
235.3   > 25 |   buildCustomFormatters,
235.3        | ^^^^^^^^^^^
235.3   > 26 |   CategoricalColorNamespace,
235.3        | ^^^^^^^^^^^
235.3   > 27 |   CurrencyFormatter,
235.3        | ^^^^^^^^^^^
235.3   > 28 |   ensureIsArray,
235.3        | ^^^^^^^^^^^
235.3   > 29 |   tooltipHtml,
235.3        | ^^^^^^^^^^^
235.3   > 30 |   GenericDataType,
235.3        | ^^^^^^^^^^^
235.3   > 31 |   getCustomFormatter,
235.3        | ^^^^^^^^^^^
235.3   > 32 |   getMetricLabel,
235.3        | ^^^^^^^^^^^
235.3   > 33 |   getNumberFormatter,
235.3        | ^^^^^^^^^^^
235.3   > 34 |   getXAxisLabel,
235.3        | ^^^^^^^^^^^
235.3   > 35 |   isDefined,
235.3        | ^^^^^^^^^^^
235.3   > 36 |   isEventAnnotationLayer,
235.3        | ^^^^^^^^^^^
235.3   > 37 |   isFormulaAnnotationLayer,
235.3        | ^^^^^^^^^^^
235.3   > 38 |   isIntervalAnnotationLayer,
235.3        | ^^^^^^^^^^^
235.3   > 39 |   isPhysicalColumn,
235.3        | ^^^^^^^^^^^
235.3   > 40 |   isTimeseriesAnnotationLayer,
235.3        | ^^^^^^^^^^^
235.3   > 41 |   t,
235.3        | ^^^^
235.3     42 |   TimeseriesChartDataResponseResult,
235.3     43 |   NumberFormats,
235.3     44 | } from '@superset-ui/core';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:23:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     21 | import {
235.3     22 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 23 |   AnnotationLayer,
235.3        |   ^^^^^^^^^^^^^^^^
235.3   > 24 |   AxisType,
235.3        | ^^^^^^^^^^^
235.3   > 25 |   buildCustomFormatters,
235.3        | ^^^^^^^^^^^
235.3   > 26 |   CategoricalColorNamespace,
235.3        | ^^^^^^^^^^^
235.3   > 27 |   CurrencyFormatter,
235.3        | ^^^^^^^^^^^
235.3   > 28 |   ensureIsArray,
235.3        | ^^^^^^^^^^^
235.3   > 29 |   tooltipHtml,
235.3        | ^^^^^^^^^^^
235.3   > 30 |   GenericDataType,
235.3        | ^^^^^^^^^^^
235.3   > 31 |   getCustomFormatter,
235.3        | ^^^^^^^^^^^
235.3   > 32 |   getMetricLabel,
235.3        | ^^^^^^^^^^^
235.3   > 33 |   getNumberFormatter,
235.3        | ^^^^^^^^^^^
235.3   > 34 |   getXAxisLabel,
235.3        | ^^^^^^^^^^^
235.3   > 35 |   isDefined,
235.3        | ^^^^^^^^^^^
235.3   > 36 |   isEventAnnotationLayer,
235.3        | ^^^^^^^^^^^
235.3   > 37 |   isFormulaAnnotationLayer,
235.3        | ^^^^^^^^^^^
235.3   > 38 |   isIntervalAnnotationLayer,
235.3        | ^^^^^^^^^^^
235.3   > 39 |   isPhysicalColumn,
235.3        | ^^^^^^^^^^^
235.3   > 40 |   isTimeseriesAnnotationLayer,
235.3        | ^^^^^^^^^^^
235.3   > 41 |   t,
235.3        | ^^^^^^^^^^^
235.3   > 42 |   TimeseriesChartDataResponseResult,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     43 |   NumberFormats,
235.3     44 | } from '@superset-ui/core';
235.3     45 | import {
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:23:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     21 | import {
235.3     22 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 23 |   AnnotationLayer,
235.3        |   ^^^^^^^^^^^^^^^^
235.3   > 24 |   AxisType,
235.3        | ^^^^^^^^^^^
235.3   > 25 |   buildCustomFormatters,
235.3        | ^^^^^^^^^^^
235.3   > 26 |   CategoricalColorNamespace,
235.3        | ^^^^^^^^^^^
235.3   > 27 |   CurrencyFormatter,
235.3        | ^^^^^^^^^^^
235.3   > 28 |   ensureIsArray,
235.3        | ^^^^^^^^^^^
235.3   > 29 |   tooltipHtml,
235.3        | ^^^^^^^^^^^
235.3   > 30 |   GenericDataType,
235.3        | ^^^^^^^^^^^
235.3   > 31 |   getCustomFormatter,
235.3        | ^^^^^^^^^^^
235.3   > 32 |   getMetricLabel,
235.3        | ^^^^^^^^^^^
235.3   > 33 |   getNumberFormatter,
235.3        | ^^^^^^^^^^^
235.3   > 34 |   getXAxisLabel,
235.3        | ^^^^^^^^^^^
235.3   > 35 |   isDefined,
235.3        | ^^^^^^^^^^^
235.3   > 36 |   isEventAnnotationLayer,
235.3        | ^^^^^^^^^^^
235.3   > 37 |   isFormulaAnnotationLayer,
235.3        | ^^^^^^^^^^^
235.3   > 38 |   isIntervalAnnotationLayer,
235.3        | ^^^^^^^^^^^
235.3   > 39 |   isPhysicalColumn,
235.3        | ^^^^^^^^^^^
235.3   > 40 |   isTimeseriesAnnotationLayer,
235.3        | ^^^^^^^^^^^
235.3   > 41 |   t,
235.3        | ^^^^^^^^^^^
235.3   > 42 |   TimeseriesChartDataResponseResult,
235.3        | ^^^^^^^^^^^
235.3   > 43 |   NumberFormats,
235.3        | ^^^^^^^^^^^^^^^^
235.3     44 | } from '@superset-ui/core';
235.3     45 | import {
235.3     46 |   extractExtraMetrics,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:24:3
235.3 TS2304: Cannot find name 'AxisType'.
235.3     22 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3     23 |   AnnotationLayer,
235.3   > 24 |   AxisType,
235.3        |   ^^^^^^^^
235.3     25 |   buildCustomFormatters,
235.3     26 |   CategoricalColorNamespace,
235.3     27 |   CurrencyFormatter,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:25:3
235.3 TS2304: Cannot find name 'buildCustomFormatters'.
235.3     23 |   AnnotationLayer,
235.3     24 |   AxisType,
235.3   > 25 |   buildCustomFormatters,
235.3        |   ^^^^^^^^^^^^^^^^^^^^^
235.3     26 |   CategoricalColorNamespace,
235.3     27 |   CurrencyFormatter,
235.3     28 |   ensureIsArray,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:26:3
235.3 TS2304: Cannot find name 'CategoricalColorNamespace'.
235.3     24 |   AxisType,
235.3     25 |   buildCustomFormatters,
235.3   > 26 |   CategoricalColorNamespace,
235.3        |   ^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     27 |   CurrencyFormatter,
235.3     28 |   ensureIsArray,
235.3     29 |   tooltipHtml,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:27:3
235.3 TS2304: Cannot find name 'CurrencyFormatter'.
235.3     25 |   buildCustomFormatters,
235.3     26 |   CategoricalColorNamespace,
235.3   > 27 |   CurrencyFormatter,
235.3        |   ^^^^^^^^^^^^^^^^^
235.3     28 |   ensureIsArray,
235.3     29 |   tooltipHtml,
235.3     30 |   GenericDataType,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:28:3
235.3 TS2304: Cannot find name 'ensureIsArray'.
235.3     26 |   CategoricalColorNamespace,
235.3     27 |   CurrencyFormatter,
235.3   > 28 |   ensureIsArray,
235.3        |   ^^^^^^^^^^^^^
235.3     29 |   tooltipHtml,
235.3     30 |   GenericDataType,
235.3     31 |   getCustomFormatter,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:29:3
235.3 TS2304: Cannot find name 'tooltipHtml'.
235.3     27 |   CurrencyFormatter,
235.3     28 |   ensureIsArray,
235.3   > 29 |   tooltipHtml,
235.3        |   ^^^^^^^^^^^
235.3     30 |   GenericDataType,
235.3     31 |   getCustomFormatter,
235.3     32 |   getMetricLabel,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:30:3
235.3 TS2304: Cannot find name 'GenericDataType'.
235.3     28 |   ensureIsArray,
235.3     29 |   tooltipHtml,
235.3   > 30 |   GenericDataType,
235.3        |   ^^^^^^^^^^^^^^^
235.3     31 |   getCustomFormatter,
235.3     32 |   getMetricLabel,
235.3     33 |   getNumberFormatter,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:31:3
235.3 TS2304: Cannot find name 'getCustomFormatter'.
235.3     29 |   tooltipHtml,
235.3     30 |   GenericDataType,
235.3   > 31 |   getCustomFormatter,
235.3        |   ^^^^^^^^^^^^^^^^^^
235.3     32 |   getMetricLabel,
235.3     33 |   getNumberFormatter,
235.3     34 |   getXAxisLabel,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:32:3
235.3 TS2304: Cannot find name 'getMetricLabel'.
235.3     30 |   GenericDataType,
235.3     31 |   getCustomFormatter,
235.3   > 32 |   getMetricLabel,
235.3        |   ^^^^^^^^^^^^^^
235.3     33 |   getNumberFormatter,
235.3     34 |   getXAxisLabel,
235.3     35 |   isDefined,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:33:3
235.3 TS2304: Cannot find name 'getNumberFormatter'.
235.3     31 |   getCustomFormatter,
235.3     32 |   getMetricLabel,
235.3   > 33 |   getNumberFormatter,
235.3        |   ^^^^^^^^^^^^^^^^^^
235.3     34 |   getXAxisLabel,
235.3     35 |   isDefined,
235.3     36 |   isEventAnnotationLayer,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:34:3
235.3 TS2304: Cannot find name 'getXAxisLabel'.
235.3     32 |   getMetricLabel,
235.3     33 |   getNumberFormatter,
235.3   > 34 |   getXAxisLabel,
235.3        |   ^^^^^^^^^^^^^
235.3     35 |   isDefined,
235.3     36 |   isEventAnnotationLayer,
235.3     37 |   isFormulaAnnotationLayer,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:35:3
235.3 TS2304: Cannot find name 'isDefined'.
235.3     33 |   getNumberFormatter,
235.3     34 |   getXAxisLabel,
235.3   > 35 |   isDefined,
235.3        |   ^^^^^^^^^
235.3     36 |   isEventAnnotationLayer,
235.3     37 |   isFormulaAnnotationLayer,
235.3     38 |   isIntervalAnnotationLayer,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:36:3
235.3 TS2304: Cannot find name 'isEventAnnotationLayer'.
235.3     34 |   getXAxisLabel,
235.3     35 |   isDefined,
235.3   > 36 |   isEventAnnotationLayer,
235.3        |   ^^^^^^^^^^^^^^^^^^^^^^
235.3     37 |   isFormulaAnnotationLayer,
235.3     38 |   isIntervalAnnotationLayer,
235.3     39 |   isPhysicalColumn,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:37:3
235.3 TS2304: Cannot find name 'isFormulaAnnotationLayer'.
235.3     35 |   isDefined,
235.3     36 |   isEventAnnotationLayer,
235.3   > 37 |   isFormulaAnnotationLayer,
235.3        |   ^^^^^^^^^^^^^^^^^^^^^^^^
235.3     38 |   isIntervalAnnotationLayer,
235.3     39 |   isPhysicalColumn,
235.3     40 |   isTimeseriesAnnotationLayer,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:38:3
235.3 TS2304: Cannot find name 'isIntervalAnnotationLayer'.
235.3     36 |   isEventAnnotationLayer,
235.3     37 |   isFormulaAnnotationLayer,
235.3   > 38 |   isIntervalAnnotationLayer,
235.3        |   ^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     39 |   isPhysicalColumn,
235.3     40 |   isTimeseriesAnnotationLayer,
235.3     41 |   t,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:39:3
235.3 TS2304: Cannot find name 'isPhysicalColumn'.
235.3     37 |   isFormulaAnnotationLayer,
235.3     38 |   isIntervalAnnotationLayer,
235.3   > 39 |   isPhysicalColumn,
235.3        |   ^^^^^^^^^^^^^^^^
235.3     40 |   isTimeseriesAnnotationLayer,
235.3     41 |   t,
235.3     42 |   TimeseriesChartDataResponseResult,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:40:3
235.3 TS2304: Cannot find name 'isTimeseriesAnnotationLayer'.
235.3     38 |   isIntervalAnnotationLayer,
235.3     39 |   isPhysicalColumn,
235.3   > 40 |   isTimeseriesAnnotationLayer,
235.3        |   ^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     41 |   t,
235.3     42 |   TimeseriesChartDataResponseResult,
235.3     43 |   NumberFormats,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:41:3
235.3 TS2304: Cannot find name 't'.
235.3     39 |   isPhysicalColumn,
235.3     40 |   isTimeseriesAnnotationLayer,
235.3   > 41 |   t,
235.3        |   ^
235.3     42 |   TimeseriesChartDataResponseResult,
235.3     43 |   NumberFormats,
235.3     44 | } from '@superset-ui/core';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:42:3
235.3 TS2304: Cannot find name 'TimeseriesChartDataResponseResult'.
235.3     40 |   isTimeseriesAnnotationLayer,
235.3     41 |   t,
235.3   > 42 |   TimeseriesChartDataResponseResult,
235.3        |   ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     43 |   NumberFormats,
235.3     44 | } from '@superset-ui/core';
235.3     45 | import {
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:43:3
235.3 TS2304: Cannot find name 'NumberFormats'.
235.3     41 |   t,
235.3     42 |   TimeseriesChartDataResponseResult,
235.3   > 43 |   NumberFormats,
235.3        |   ^^^^^^^^^^^^^
235.3     44 | } from '@superset-ui/core';
235.3     45 | import {
235.3     46 |   extractExtraMetrics,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:44:3
235.3 TS2304: Cannot find name 'from'.
235.3     42 |   TimeseriesChartDataResponseResult,
235.3     43 |   NumberFormats,
235.3   > 44 | } from '@superset-ui/core';
235.3        |   ^^^^
235.3     45 | import {
235.3     46 |   extractExtraMetrics,
235.3     47 |   getOriginalSeries,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:140:18
235.3 TS2304: Cannot find name 'TimeseriesChartDataResponseResult'.
235.3     138 |   const [queryData] = queriesData;
235.3     139 |   const { data = [], label_map = {} } =
235.3   > 140 |     queryData as TimeseriesChartDataResponseResult;
235.3         |                  ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     141 |
235.3     142 |   const dataTypes = getColtypesMapping(queryData);
235.3     143 |   const annotationData = getAnnotationData(chartProps);
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:225:19
235.3 TS2304: Cannot find name 'ensureIsArray'.
235.3     223 | }
235.3     224 |   const refs: Refs = {};
235.3   > 225 |   const groupBy = ensureIsArray(groupby);
235.3         |                   ^^^^^^^^^^^^^
235.3     226 |   const labelMap: { [key: string]: string[] } = Object.entries(
235.3     227 |     label_map,
235.3     228 |   ).reduce((acc, entry) => {
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:230:16
235.3 TS2339: Property 'length' does not exist on type 'unknown'.
235.3     228 |   ).reduce((acc, entry) => {
235.3     229 |     if (
235.3   > 230 |       entry[1].length > groupBy.length &&
235.3         |                ^^^^^^
235.3     231 |       Array.isArray(timeCompare) &&
235.3     232 |       timeCompare.includes(entry[1][0])
235.3     233 |     ) {
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:234:16
235.3 TS2339: Property 'shift' does not exist on type 'unknown'.
235.3     232 |       timeCompare.includes(entry[1][0])
235.3     233 |     ) {
235.3   > 234 |       entry[1].shift();
235.3         |                ^^^^^
235.3     235 |     }
235.3     236 |     return { ...acc, [entry[0]]: entry[1] };
235.3     237 |   }, {});
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:238:22
235.3 TS2304: Cannot find name 'CategoricalColorNamespace'.
235.3     236 |     return { ...acc, [entry[0]]: entry[1] };
235.3     237 |   }, {});
235.3   > 238 |   const colorScale = CategoricalColorNamespace.getScale(colorScheme as string);
235.3         |                      ^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     239 |   const rebasedData = rebaseForecastDatum(data, verboseMap);
235.3     240 |   let xAxisLabel = getXAxisLabel(chartProps.rawFormData) as string;
235.3     241 |   if (
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:240:20
235.3 TS2304: Cannot find name 'getXAxisLabel'.
235.3     238 |   const colorScale = CategoricalColorNamespace.getScale(colorScheme as string);
235.3     239 |   const rebasedData = rebaseForecastDatum(data, verboseMap);
235.3   > 240 |   let xAxisLabel = getXAxisLabel(chartProps.rawFormData) as string;
235.3         |                    ^^^^^^^^^^^^^
235.3     241 |   if (
235.3     242 |     isPhysicalColumn(chartProps.rawFormData?.x_axis) &&
235.3     243 |     isDefined(verboseMap[xAxisLabel])
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:242:5
235.3 TS2304: Cannot find name 'isPhysicalColumn'.
235.3     240 |   let xAxisLabel = getXAxisLabel(chartProps.rawFormData) as string;
235.3     241 |   if (
235.3   > 242 |     isPhysicalColumn(chartProps.rawFormData?.x_axis) &&
235.3         |     ^^^^^^^^^^^^^^^^
235.3     243 |     isDefined(verboseMap[xAxisLabel])
235.3     244 |   ) {
235.3     245 |     xAxisLabel = verboseMap[xAxisLabel];
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:243:5
235.3 TS2304: Cannot find name 'isDefined'.
235.3     241 |   if (
235.3     242 |     isPhysicalColumn(chartProps.rawFormData?.x_axis) &&
235.3   > 243 |     isDefined(verboseMap[xAxisLabel])
235.3         |     ^^^^^^^^^
235.3     244 |   ) {
235.3     245 |     xAxisLabel = verboseMap[xAxisLabel];
235.3     246 |   }
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:258:5
235.3 TS2304: Cannot find name 'getMetricLabel'.
235.3     256 |   );
235.3     257 |   const extraMetricLabels = extractExtraMetrics(chartProps.rawFormData).map(
235.3   > 258 |     getMetricLabel,
235.3         |     ^^^^^^^^^^^^^^
235.3     259 |   );
235.3     260 |
235.3     261 |   const isMultiSeries = groupBy.length || metrics?.length > 1;
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:268:7
235.3 TS2322: Type 'unknown[]' is not assignable to type 'string[]'.
235.3   Type 'unknown' is not assignable to type 'string'.
235.3     266 |       fillNeighborValue: stack && !forecastEnabled ? 0 : undefined,
235.3     267 |       xAxis: xAxisLabel,
235.3   > 268 |       extraMetricLabels,
235.3         |       ^^^^^^^^^^^^^^^^^
235.3     269 |       stack,
235.3     270 |       totalStackedValues,
235.3     271 |       isHorizontal,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:296:27
235.3 TS2304: Cannot find name 'NumberFormats'.
235.3     294 |   const percentFormatter = forcePercentFormatter
235.3     295 |     ? getPercentFormatter(yAxisFormat)
235.3   > 296 |     : getPercentFormatter(NumberFormats.PERCENT_2_POINT);
235.3         |                           ^^^^^^^^^^^^^
235.3     297 |   const defaultFormatter = currencyFormat?.symbol
235.3     298 |     ? new CurrencyFormatter({ d3Format: yAxisFormat, currency: currencyFormat })
235.3     299 |     : getNumberFormatter(yAxisFormat);
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:298:11
235.3 TS2304: Cannot find name 'CurrencyFormatter'.
235.3     296 |     : getPercentFormatter(NumberFormats.PERCENT_2_POINT);
235.3     297 |   const defaultFormatter = currencyFormat?.symbol
235.3   > 298 |     ? new CurrencyFormatter({ d3Format: yAxisFormat, currency: currencyFormat })
235.3         |           ^^^^^^^^^^^^^^^^^
235.3     299 |     : getNumberFormatter(yAxisFormat);
235.3     300 |   const customFormatters = buildCustomFormatters(
235.3     301 |     metrics,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:299:7
235.3 TS2304: Cannot find name 'getNumberFormatter'.
235.3     297 |   const defaultFormatter = currencyFormat?.symbol
235.3     298 |     ? new CurrencyFormatter({ d3Format: yAxisFormat, currency: currencyFormat })
235.3   > 299 |     : getNumberFormatter(yAxisFormat);
235.3         |       ^^^^^^^^^^^^^^^^^^
235.3     300 |   const customFormatters = buildCustomFormatters(
235.3     301 |     metrics,
235.3     302 |     currencyFormats,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:300:28
235.3 TS2304: Cannot find name 'buildCustomFormatters'.
235.3     298 |     ? new CurrencyFormatter({ d3Format: yAxisFormat, currency: currencyFormat })
235.3     299 |     : getNumberFormatter(yAxisFormat);
235.3   > 300 |   const customFormatters = buildCustomFormatters(
235.3         |                            ^^^^^^^^^^^^^^^^^^^^^
235.3     301 |     metrics,
235.3     302 |     currencyFormats,
235.3     303 |     columnFormats,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:308:17
235.3 TS2304: Cannot find name 'ensureIsArray'.
235.3     306 |   );
235.3     307 |
235.3   > 308 |   const array = ensureIsArray(chartProps.rawFormData?.time_compare);
235.3         |                 ^^^^^^^^^^^^^
235.3     309 |   const inverted = invert(verboseMap);
235.3     310 |
235.3     311 |   let patternIncrement = 0;
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:344:14
235.3 TS2304: Cannot find name 'getCustomFormatter'.
235.3     342 |         formatter: forcePercentFormatter
235.3     343 |           ? percentFormatter
235.3   > 344 |           : (getCustomFormatter(
235.3         |              ^^^^^^^^^^^^^^^^^^
235.3     345 |             customFormatters,
235.3     346 |             metrics,
235.3     347 |             labelMap?.[seriesName]?.[0],
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:397:21
235.3 TS2304: Cannot find name 'AnnotationLayer'.
235.3     395 |
235.3     396 |   annotationLayers
235.3   > 397 |     .filter((layer: AnnotationLayer) => layer.show)
235.3         |                     ^^^^^^^^^^^^^^^
235.3     398 |     .forEach((layer: AnnotationLayer) => {
235.3     399 |       if (isFormulaAnnotationLayer(layer))
235.3     400 |         series.push(
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:398:22
235.3 TS2304: Cannot find name 'AnnotationLayer'.
235.3     396 |   annotationLayers
235.3     397 |     .filter((layer: AnnotationLayer) => layer.show)
235.3   > 398 |     .forEach((layer: AnnotationLayer) => {
235.3         |                      ^^^^^^^^^^^^^^^
235.3     399 |       if (isFormulaAnnotationLayer(layer))
235.3     400 |         series.push(
235.3     401 |           transformFormulaAnnotation(
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:399:11
235.3 TS2304: Cannot find name 'isFormulaAnnotationLayer'.
235.3     397 |     .filter((layer: AnnotationLayer) => layer.show)
235.3     398 |     .forEach((layer: AnnotationLayer) => {
235.3   > 399 |       if (isFormulaAnnotationLayer(layer))
235.3         |           ^^^^^^^^^^^^^^^^^^^^^^^^
235.3     400 |         series.push(
235.3     401 |           transformFormulaAnnotation(
235.3     402 |             layer,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:411:16
235.3 TS2304: Cannot find name 'isIntervalAnnotationLayer'.
235.3     409 |           ),
235.3     410 |         );
235.3   > 411 |       else if (isIntervalAnnotationLayer(layer)) {
235.3         |                ^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     412 |         series.push(
235.3     413 |           ...transformIntervalAnnotation(
235.3     414 |             layer,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:423:18
235.3 TS2304: Cannot find name 'isEventAnnotationLayer'.
235.3     421 |           ),
235.3     422 |         );
235.3   > 423 |       } else if (isEventAnnotationLayer(layer)) {
235.3         |                  ^^^^^^^^^^^^^^^^^^^^^^
235.3     424 |         series.push(
235.3     425 |           ...transformEventAnnotation(
235.3     426 |             layer,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:435:18
235.3 TS2304: Cannot find name 'isTimeseriesAnnotationLayer'.
235.3     433 |           ),
235.3     434 |         );
235.3   > 435 |       } else if (isTimeseriesAnnotationLayer(layer)) {
235.3         |                  ^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     436 |         series.push(
235.3     437 |           ...transformTimeseriesAnnotation(
235.3     438 |             layer,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:484:23
235.3 TS2304: Cannot find name 'GenericDataType'.
235.3     482 |
235.3     483 |   const tooltipFormatter =
235.3   > 484 |     xAxisDataType === GenericDataType.Temporal
235.3         |                       ^^^^^^^^^^^^^^^
235.3     485 |       ? getTooltipTimeFormatter(tooltipTimeFormat)
235.3     486 |       : String;
235.3     487 |   const xAxisFormatter =
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:488:23
235.3 TS2304: Cannot find name 'GenericDataType'.
235.3     486 |       : String;
235.3     487 |   const xAxisFormatter =
235.3   > 488 |     xAxisDataType === GenericDataType.Temporal
235.3         |                       ^^^^^^^^^^^^^^^
235.3     489 |       ? getXAxisFormatter(xAxisTimeFormat)
235.3     490 |       : String;
235.3     491 |
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:536:21
235.3 TS2304: Cannot find name 'AxisType'.
235.3     534 |     minorTick: { show: minorTicks },
235.3     535 |     minInterval:
235.3   > 536 |       xAxisType === AxisType.Time && timeGrainSqla
235.3         |                     ^^^^^^^^
235.3     537 |         ? TIMEGRAIN_TO_TIMESTAMP[
235.3     538 |         timeGrainSqla as keyof typeof TIMEGRAIN_TO_TIMESTAMP
235.3     539 |         ]
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:552:21
235.3 TS2304: Cannot find name 'AxisType'.
235.3     550 |   let yAxis: any = {
235.3     551 |     ...defaultYAxis,
235.3   > 552 |     type: logAxis ? AxisType.Log : AxisType.Value,
235.3         |                     ^^^^^^^^
235.3     553 |     min: yAxisMin,
235.3     554 |     max: yAxisMax,
235.3     555 |     minorTick: { show: minorTicks },
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:552:36
235.3 TS2304: Cannot find name 'AxisType'.
235.3     550 |   let yAxis: any = {
235.3     551 |     ...defaultYAxis,
235.3   > 552 |     type: logAxis ? AxisType.Log : AxisType.Value,
235.3         |                                    ^^^^^^^^
235.3     553 |     min: yAxisMin,
235.3     554 |     max: yAxisMax,
235.3     555 |     minorTick: { show: minorTicks },
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:593:36
235.3 TS2304: Cannot find name 'ensureIsArray'.
235.3     591 |
235.3     592 |         const [xIndex, yIndex] = isHorizontal ? [1, 0] : [0, 1];
235.3   > 593 |         const extraTooltipFields = ensureIsArray(formData.extra_tooltip_field);
235.3         |                                    ^^^^^^^^^^^^^
235.3     594 |
235.3     595 |         const xValue: number = richTooltip
235.3     596 |           ? params[0].value?.[xIndex]
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:618:13
235.3 TS2304: Cannot find name 'getCustomFormatter'.
235.3     616 |         const formatter = forcePercentFormatter
235.3     617 |           ? percentFormatter
235.3   > 618 |           : getCustomFormatter(customFormatters, metrics) ?? defaultFormatter;
235.3         |             ^^^^^^^^^^^^^^^^^^
235.3     619 |
235.3     620 |         const rows: string[][] = [];
235.3     621 |         const total = Object.values(forecastValues).reduce(
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:680:16
235.3 TS2304: Cannot find name 'tooltipHtml'.
235.3     678 |
235.3     679 |         console.log('🧪 Final tooltip rows:', rows);
235.3   > 680 |         return tooltipHtml(rows, tooltipFormatter(xValue), focusedRow);
235.3         |                ^^^^^^^^^^^
235.3     681 |       },
235.3     682 |     },
235.3     683 |
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:723:19
235.3 TS2304: Cannot find name 't'.
235.3     721 |           ...(stack ? { yAxisIndex: false } : {}), // disable y-axis zoom for stacked charts
235.3     722 |           title: {
235.3   > 723 |             zoom: t('zoom area'),
235.3         |                   ^
235.3     724 |             back: t('restore zoom'),
235.3     725 |           },
235.3     726 |         },
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/transformProps.ts:724:19
235.3 TS2304: Cannot find name 't'.
235.3     722 |           title: {
235.3     723 |             zoom: t('zoom area'),
235.3   > 724 |             back: t('restore zoom'),
235.3         |                   ^
235.3     725 |           },
235.3     726 |         },
235.3     727 |       },
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/types.ts:21:8
235.3 TS1141: String literal expected.
235.3     19 | import type { OptionName } from 'echarts/types/src/util/types';
235.3     20 | import {
235.3   > 21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3        |        ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     22 |   AnnotationLayer,
235.3     23 |   AxisType,
235.3     24 |   ContributionType,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/types.ts:21:118
235.3 TS2304: Cannot find name 'from'.
235.3     19 | import type { OptionName } from 'echarts/types/src/util/types';
235.3     20 | import {
235.3   > 21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3        |                                                                                                                      ^^^^
235.3     22 |   AnnotationLayer,
235.3     23 |   AxisType,
235.3     24 |   ContributionType,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/types.ts:22:3
235.3 TS2304: Cannot find name 'AnnotationLayer'.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   AnnotationLayer,
235.3        |   ^^^^^^^^^^^^^^^
235.3     23 |   AxisType,
235.3     24 |   ContributionType,
235.3     25 |   QueryFormData,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/types.ts:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   AnnotationLayer,
235.3        |   ^^^^^^^^^^^^^^^
235.3     23 |   AxisType,
235.3     24 |   ContributionType,
235.3     25 |   QueryFormData,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/types.ts:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   AnnotationLayer,
235.3        |   ^^^^^^^^^^^^^^^^
235.3   > 23 |   AxisType,
235.3        | ^^^^^^^^^^^
235.3     24 |   ContributionType,
235.3     25 |   QueryFormData,
235.3     26 |   QueryFormMetric,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/types.ts:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   AnnotationLayer,
235.3        |   ^^^^^^^^^^^^^^^^
235.3   > 23 |   AxisType,
235.3        | ^^^^^^^^^^^
235.3   > 24 |   ContributionType,
235.3        | ^^^^^^^^^^^^^^^^^^^
235.3     25 |   QueryFormData,
235.3     26 |   QueryFormMetric,
235.3     27 |   TimeFormatter,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/types.ts:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   AnnotationLayer,
235.3        |   ^^^^^^^^^^^^^^^^
235.3   > 23 |   AxisType,
235.3        | ^^^^^^^^^^^
235.3   > 24 |   ContributionType,
235.3        | ^^^^^^^^^^^
235.3   > 25 |   QueryFormData,
235.3        | ^^^^^^^^^^^^^^^^
235.3     26 |   QueryFormMetric,
235.3     27 |   TimeFormatter,
235.3     28 |   TimeGranularity,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/types.ts:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   AnnotationLayer,
235.3        |   ^^^^^^^^^^^^^^^^
235.3   > 23 |   AxisType,
235.3        | ^^^^^^^^^^^
235.3   > 24 |   ContributionType,
235.3        | ^^^^^^^^^^^
235.3   > 25 |   QueryFormData,
235.3        | ^^^^^^^^^^^
235.3   > 26 |   QueryFormMetric,
235.3        | ^^^^^^^^^^^^^^^^^^
235.3     27 |   TimeFormatter,
235.3     28 |   TimeGranularity,
235.3     29 | } from '@superset-ui/core';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/types.ts:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   AnnotationLayer,
235.3        |   ^^^^^^^^^^^^^^^^
235.3   > 23 |   AxisType,
235.3        | ^^^^^^^^^^^
235.3   > 24 |   ContributionType,
235.3        | ^^^^^^^^^^^
235.3   > 25 |   QueryFormData,
235.3        | ^^^^^^^^^^^
235.3   > 26 |   QueryFormMetric,
235.3        | ^^^^^^^^^^^
235.3   > 27 |   TimeFormatter,
235.3        | ^^^^^^^^^^^^^^^^
235.3     28 |   TimeGranularity,
235.3     29 | } from '@superset-ui/core';
235.3     30 | import {
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/types.ts:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   AnnotationLayer,
235.3        |   ^^^^^^^^^^^^^^^^
235.3   > 23 |   AxisType,
235.3        | ^^^^^^^^^^^
235.3   > 24 |   ContributionType,
235.3        | ^^^^^^^^^^^
235.3   > 25 |   QueryFormData,
235.3        | ^^^^^^^^^^^
235.3   > 26 |   QueryFormMetric,
235.3        | ^^^^^^^^^^^
235.3   > 27 |   TimeFormatter,
235.3        | ^^^^^^^^^^^
235.3   > 28 |   TimeGranularity,
235.3        | ^^^^^^^^^^^^^^^^^^
235.3     29 | } from '@superset-ui/core';
235.3     30 | import {
235.3     31 |   BaseChartProps,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/types.ts:23:3
235.3 TS2304: Cannot find name 'AxisType'.
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3     22 |   AnnotationLayer,
235.3   > 23 |   AxisType,
235.3        |   ^^^^^^^^
235.3     24 |   ContributionType,
235.3     25 |   QueryFormData,
235.3     26 |   QueryFormMetric,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/types.ts:24:3
235.3 TS2304: Cannot find name 'ContributionType'.
235.3     22 |   AnnotationLayer,
235.3     23 |   AxisType,
235.3   > 24 |   ContributionType,
235.3        |   ^^^^^^^^^^^^^^^^
235.3     25 |   QueryFormData,
235.3     26 |   QueryFormMetric,
235.3     27 |   TimeFormatter,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/types.ts:25:3
235.3 TS2304: Cannot find name 'QueryFormData'.
235.3     23 |   AxisType,
235.3     24 |   ContributionType,
235.3   > 25 |   QueryFormData,
235.3        |   ^^^^^^^^^^^^^
235.3     26 |   QueryFormMetric,
235.3     27 |   TimeFormatter,
235.3     28 |   TimeGranularity,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/types.ts:26:3
235.3 TS2304: Cannot find name 'QueryFormMetric'.
235.3     24 |   ContributionType,
235.3     25 |   QueryFormData,
235.3   > 26 |   QueryFormMetric,
235.3        |   ^^^^^^^^^^^^^^^
235.3     27 |   TimeFormatter,
235.3     28 |   TimeGranularity,
235.3     29 | } from '@superset-ui/core';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/types.ts:27:3
235.3 TS2304: Cannot find name 'TimeFormatter'.
235.3     25 |   QueryFormData,
235.3     26 |   QueryFormMetric,
235.3   > 27 |   TimeFormatter,
235.3        |   ^^^^^^^^^^^^^
235.3     28 |   TimeGranularity,
235.3     29 | } from '@superset-ui/core';
235.3     30 | import {
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/types.ts:28:3
235.3 TS2304: Cannot find name 'TimeGranularity'.
235.3     26 |   QueryFormMetric,
235.3     27 |   TimeFormatter,
235.3   > 28 |   TimeGranularity,
235.3        |   ^^^^^^^^^^^^^^^
235.3     29 | } from '@superset-ui/core';
235.3     30 | import {
235.3     31 |   BaseChartProps,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/types.ts:29:3
235.3 TS2304: Cannot find name 'from'.
235.3     27 |   TimeFormatter,
235.3     28 |   TimeGranularity,
235.3   > 29 | } from '@superset-ui/core';
235.3        |   ^^^^
235.3     30 | import {
235.3     31 |   BaseChartProps,
235.3     32 |   BaseTransformedProps,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/types.ts:55:41
235.3 TS2304: Cannot find name 'QueryFormData'.
235.3     53 | }
235.3     54 |
235.3   > 55 | export type EchartsTimeseriesFormData = QueryFormData & {
235.3        |                                         ^^^^^^^^^^^^^
235.3     56 |   annotationLayers: AnnotationLayer[];
235.3     57 |   area: boolean;
235.3     58 |   colorScheme?: string;
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/types.ts:56:21
235.3 TS2304: Cannot find name 'AnnotationLayer'.
235.3     54 |
235.3     55 | export type EchartsTimeseriesFormData = QueryFormData & {
235.3   > 56 |   annotationLayers: AnnotationLayer[];
235.3        |                     ^^^^^^^^^^^^^^^
235.3     57 |   area: boolean;
235.3     58 |   colorScheme?: string;
235.3     59 |   timeShiftColor?: boolean;
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/types.ts:60:22
235.3 TS2304: Cannot find name 'ContributionType'.
235.3     58 |   colorScheme?: string;
235.3     59 |   timeShiftColor?: boolean;
235.3   > 60 |   contributionMode?: ContributionType;
235.3        |                      ^^^^^^^^^^^^^^^^
235.3     61 |   forecastEnabled: boolean;
235.3     62 |   forecastPeriods: number;
235.3     63 |   forecastInterval: number;
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/types.ts:70:12
235.3 TS2304: Cannot find name 'QueryFormMetric'.
235.3     68 |   markerEnabled: boolean;
235.3     69 |   markerSize: number;
235.3   > 70 |   metrics: QueryFormMetric[];
235.3        |            ^^^^^^^^^^^^^^^
235.3     71 |   minorSplitLine: boolean;
235.3     72 |   minorTicks: boolean;
235.3     73 |   opacity: number;
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/types.ts:88:19
235.3 TS2304: Cannot find name 'TimeGranularity'.
235.3     86 |   xAxisForceCategorical?: boolean;
235.3     87 |   xAxisTimeFormat?: string;
235.3   > 88 |   timeGrainSqla?: TimeGranularity;
235.3        |                   ^^^^^^^^^^^^^^^
235.3     89 |   xAxisBounds: [number | undefined | null, number | undefined | null];
235.3     90 |   yAxisBounds: [number | undefined | null, number | undefined | null];
235.3     91 |   zoomable: boolean;
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/types.ts:113:24
235.3 TS2304: Cannot find name 'TimeFormatter'.
235.3     111 |     CrossFilterTransformedProps & {
235.3     112 |       legendData?: OptionName[];
235.3   > 113 |       xValueFormatter: TimeFormatter | StringConstructor;
235.3         |                        ^^^^^^^^^^^^^
235.3     114 |       xAxis: {
235.3     115 |         label: string;
235.3     116 |         type: AxisType;
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Timeseries/types.ts:116:15
235.3 TS2304: Cannot find name 'AxisType'.
235.3     114 |       xAxis: {
235.3     115 |         label: string;
235.3   > 116 |         type: AxisType;
235.3         |               ^^^^^^^^
235.3     117 |       };
235.3     118 |       onFocusedSeries: (series: string | null) => void;
235.3     119 |     };
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Tree/buildQuery.ts:19:29
235.3 TS2300: Duplicate identifier 'QueryFormData'.
235.3     17 |  * under the License.
235.3     18 |  */
235.3   > 19 | import { buildQueryContext, QueryFormData } from '@superset-ui/core';
235.3        |                             ^^^^^^^^^^^^^
235.3     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3     21 |
235.3     22 | export default function buildQuery(formData: QueryFormData) {
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Tree/buildQuery.ts:20:27
235.3 TS2300: Duplicate identifier 'QueryFormData'.
235.3     18 |  */
235.3     19 | import { buildQueryContext, QueryFormData } from '@superset-ui/core';
235.3   > 20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3        |                           ^^^^^^^^^^^^^
235.3     21 |
235.3     22 | export default function buildQuery(formData: QueryFormData) {
235.3     23 |   return buildQueryContext(formData, {
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Tree/controlPanel.tsx:21:8
235.3 TS1141: String literal expected.
235.3     19 | import { t } from '@superset-ui/core';
235.3     20 | import {
235.3   > 21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3        |        ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     22 |   ControlPanelConfig,
235.3     23 |   ControlSubSectionHeader,
235.3     24 |   getStandardizedControls,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Tree/controlPanel.tsx:21:118
235.3 TS2304: Cannot find name 'from'.
235.3     19 | import { t } from '@superset-ui/core';
235.3     20 | import {
235.3   > 21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3        |                                                                                                                      ^^^^
235.3     22 |   ControlPanelConfig,
235.3     23 |   ControlSubSectionHeader,
235.3     24 |   getStandardizedControls,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Tree/controlPanel.tsx:22:3
235.3 TS2304: Cannot find name 'ControlPanelConfig'.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   ControlPanelConfig,
235.3        |   ^^^^^^^^^^^^^^^^^^
235.3     23 |   ControlSubSectionHeader,
235.3     24 |   getStandardizedControls,
235.3     25 |   sharedControls,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Tree/controlPanel.tsx:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   ControlPanelConfig,
235.3        |   ^^^^^^^^^^^^^^^^^^
235.3     23 |   ControlSubSectionHeader,
235.3     24 |   getStandardizedControls,
235.3     25 |   sharedControls,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Tree/controlPanel.tsx:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   ControlPanelConfig,
235.3        |   ^^^^^^^^^^^^^^^^^^^
235.3   > 23 |   ControlSubSectionHeader,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     24 |   getStandardizedControls,
235.3     25 |   sharedControls,
235.3     26 | } from '@superset-ui/chart-controls';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Tree/controlPanel.tsx:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   ControlPanelConfig,
235.3        |   ^^^^^^^^^^^^^^^^^^^
235.3   > 23 |   ControlSubSectionHeader,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 24 |   getStandardizedControls,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     25 |   sharedControls,
235.3     26 | } from '@superset-ui/chart-controls';
235.3     27 | import { DEFAULT_FORM_DATA } from './constants';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Tree/controlPanel.tsx:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   ControlPanelConfig,
235.3        |   ^^^^^^^^^^^^^^^^^^^
235.3   > 23 |   ControlSubSectionHeader,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 24 |   getStandardizedControls,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 25 |   sharedControls,
235.3        | ^^^^^^^^^^^^^^^^^
235.3     26 | } from '@superset-ui/chart-controls';
235.3     27 | import { DEFAULT_FORM_DATA } from './constants';
235.3     28 |
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Tree/controlPanel.tsx:23:3
235.3 TS2304: Cannot find name 'ControlSubSectionHeader'.
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3     22 |   ControlPanelConfig,
235.3   > 23 |   ControlSubSectionHeader,
235.3        |   ^^^^^^^^^^^^^^^^^^^^^^^
235.3     24 |   getStandardizedControls,
235.3     25 |   sharedControls,
235.3     26 | } from '@superset-ui/chart-controls';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Tree/controlPanel.tsx:24:3
235.3 TS2304: Cannot find name 'getStandardizedControls'.
235.3     22 |   ControlPanelConfig,
235.3     23 |   ControlSubSectionHeader,
235.3   > 24 |   getStandardizedControls,
235.3        |   ^^^^^^^^^^^^^^^^^^^^^^^
235.3     25 |   sharedControls,
235.3     26 | } from '@superset-ui/chart-controls';
235.3     27 | import { DEFAULT_FORM_DATA } from './constants';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Tree/controlPanel.tsx:25:3
235.3 TS2304: Cannot find name 'sharedControls'.
235.3     23 |   ControlSubSectionHeader,
235.3     24 |   getStandardizedControls,
235.3   > 25 |   sharedControls,
235.3        |   ^^^^^^^^^^^^^^
235.3     26 | } from '@superset-ui/chart-controls';
235.3     27 | import { DEFAULT_FORM_DATA } from './constants';
235.3     28 |
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Tree/controlPanel.tsx:26:3
235.3 TS2304: Cannot find name 'from'.
235.3     24 |   getStandardizedControls,
235.3     25 |   sharedControls,
235.3   > 26 | } from '@superset-ui/chart-controls';
235.3        |   ^^^^
235.3     27 | import { DEFAULT_FORM_DATA } from './constants';
235.3     28 |
235.3     29 | const requiredEntity = {
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Tree/controlPanel.tsx:30:6
235.3 TS2304: Cannot find name 'sharedControls'.
235.3     28 |
235.3     29 | const requiredEntity = {
235.3   > 30 |   ...sharedControls.entity,
235.3        |      ^^^^^^^^^^^^^^
235.3     31 |   clearable: false,
235.3     32 | };
235.3     33 | const optionalEntity = {
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Tree/controlPanel.tsx:34:6
235.3 TS2304: Cannot find name 'sharedControls'.
235.3     32 | };
235.3     33 | const optionalEntity = {
235.3   > 34 |   ...sharedControls.entity,
235.3        |      ^^^^^^^^^^^^^^
235.3     35 |   clearable: true,
235.3     36 |   validators: [],
235.3     37 | };
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Tree/controlPanel.tsx:39:21
235.3 TS2304: Cannot find name 'ControlPanelConfig'.
235.3     37 | };
235.3     38 |
235.3   > 39 | const controlPanel: ControlPanelConfig = {
235.3        |                     ^^^^^^^^^^^^^^^^^^
235.3     40 |   controlPanelSections: [
235.3     41 |     {
235.3     42 |       label: t('Query'),
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Tree/controlPanel.tsx:93:18
235.3 TS2304: Cannot find name 'sharedControls'.
235.3     91 |             name: 'metric',
235.3     92 |             config: {
235.3   > 93 |               ...sharedControls.metric,
235.3        |                  ^^^^^^^^^^^^^^
235.3     94 |               clearable: true,
235.3     95 |               validators: [],
235.3     96 |               description: t('Metric for node values'),
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Tree/controlPanel.tsx:108:11
235.3 TS2304: Cannot find name 'ControlSubSectionHeader'.
235.3     106 |       expanded: true,
235.3     107 |       controlSetRows: [
235.3   > 108 |         [<ControlSubSectionHeader>{t('Layout')}</ControlSubSectionHeader>],
235.3         |           ^^^^^^^^^^^^^^^^^^^^^^^
235.3     109 |         [
235.3     110 |           {
235.3     111 |             name: 'layout',
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Tree/controlPanel.tsx:108:50
235.3 TS2304: Cannot find name 'ControlSubSectionHeader'.
235.3     106 |       expanded: true,
235.3     107 |       controlSetRows: [
235.3   > 108 |         [<ControlSubSectionHeader>{t('Layout')}</ControlSubSectionHeader>],
235.3         |                                                  ^^^^^^^^^^^^^^^^^^^^^^^
235.3     109 |         [
235.3     110 |           {
235.3     111 |             name: 'layout',
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Tree/controlPanel.tsx:288:13
235.3 TS2304: Cannot find name 'getStandardizedControls'.
235.3     286 |   formDataOverrides: formData => ({
235.3     287 |     ...formData,
235.3   > 288 |     metric: getStandardizedControls().shiftMetric(),
235.3         |             ^^^^^^^^^^^^^^^^^^^^^^^
235.3     289 |   }),
235.3     290 | };
235.3     291 |
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Tree/types.ts:21:35
235.3 TS2300: Duplicate identifier 'QueryFormData'.
235.3     19 | import type { OptionName } from 'echarts/types/src/util/types';
235.3     20 | import type { TreeSeriesNodeItemOption } from 'echarts/types/src/chart/tree/TreeSeries';
235.3   > 21 | import { ChartDataResponseResult, QueryFormData } from '@superset-ui/core';
235.3        |                                   ^^^^^^^^^^^^^
235.3     22 | import { BaseChartProps, BaseTransformedProps } from '../types';
235.3     23 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3     24 |
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Tree/types.ts:23:27
235.3 TS2300: Duplicate identifier 'QueryFormData'.
235.3     21 | import { ChartDataResponseResult, QueryFormData } from '@superset-ui/core';
235.3     22 | import { BaseChartProps, BaseTransformedProps } from '../types';
235.3   > 23 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3        |                           ^^^^^^^^^^^^^
235.3     24 |
235.3     25 | export type EchartsTreeFormData = QueryFormData & {
235.3     26 |   id: string;
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Treemap/buildQuery.ts:19:29
235.3 TS2300: Duplicate identifier 'QueryFormData'.
235.3     17 |  * under the License.
235.3     18 |  */
235.3   > 19 | import { buildQueryContext, QueryFormData } from '@superset-ui/core';
235.3        |                             ^^^^^^^^^^^^^
235.3     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3     21 |
235.3     22 | export default function buildQuery(formData: QueryFormData) {
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Treemap/buildQuery.ts:20:27
235.3 TS2300: Duplicate identifier 'QueryFormData'.
235.3     18 |  */
235.3     19 | import { buildQueryContext, QueryFormData } from '@superset-ui/core';
235.3   > 20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3        |                           ^^^^^^^^^^^^^
235.3     21 |
235.3     22 | export default function buildQuery(formData: QueryFormData) {
235.3     23 |   const { metric, sort_by_metric } = formData;
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Treemap/index.ts:32:3
235.3 TS2344: Type 'EchartsTreemapChartProps' does not satisfy the constraint 'ChartProps<PlainObject>'.
235.3   Type 'EchartsTreemapChartProps' is missing the following properties from type 'ChartProps<PlainObject>': annotationData, datasource, rawDatasource, initialValues, and 8 more.
235.3     30 | export default class EchartsTreemapChartPlugin extends EchartsChartPlugin<
235.3     31 |   EchartsTreemapFormData,
235.3   > 32 |   EchartsTreemapChartProps
235.3        |   ^^^^^^^^^^^^^^^^^^^^^^^^
235.3     33 | > {
235.3     34 |   /**
235.3     35 |    * The constructor is used to pass relevant metadata and callbacks that get
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Treemap/transformProps.ts:113:5
235.3 TS2339: Property 'height' does not exist on type 'EchartsTreemapChartProps'.
235.3     111 |   const {
235.3     112 |     formData,
235.3   > 113 |     height,
235.3         |     ^^^^^^
235.3     114 |     queriesData,
235.3     115 |     width,
235.3     116 |     hooks,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Treemap/transformProps.ts:115:5
235.3 TS2339: Property 'width' does not exist on type 'EchartsTreemapChartProps'.
235.3     113 |     height,
235.3     114 |     queriesData,
235.3   > 115 |     width,
235.3         |     ^^^^^
235.3     116 |     hooks,
235.3     117 |     filterState,
235.3     118 |     theme,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Treemap/transformProps.ts:116:5
235.3 TS2339: Property 'hooks' does not exist on type 'EchartsTreemapChartProps'.
235.3     114 |     queriesData,
235.3     115 |     width,
235.3   > 116 |     hooks,
235.3         |     ^^^^^
235.3     117 |     filterState,
235.3     118 |     theme,
235.3     119 |     inContextMenu,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Treemap/transformProps.ts:117:5
235.3 TS2339: Property 'filterState' does not exist on type 'EchartsTreemapChartProps'.
235.3     115 |     width,
235.3     116 |     hooks,
235.3   > 117 |     filterState,
235.3         |     ^^^^^^^^^^^
235.3     118 |     theme,
235.3     119 |     inContextMenu,
235.3     120 |     emitCrossFilters,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Treemap/transformProps.ts:118:5
235.3 TS2339: Property 'theme' does not exist on type 'EchartsTreemapChartProps'.
235.3     116 |     hooks,
235.3     117 |     filterState,
235.3   > 118 |     theme,
235.3         |     ^^^^^
235.3     119 |     inContextMenu,
235.3     120 |     emitCrossFilters,
235.3     121 |     datasource,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Treemap/transformProps.ts:119:5
235.3 TS2339: Property 'inContextMenu' does not exist on type 'EchartsTreemapChartProps'.
235.3     117 |     filterState,
235.3     118 |     theme,
235.3   > 119 |     inContextMenu,
235.3         |     ^^^^^^^^^^^^^
235.3     120 |     emitCrossFilters,
235.3     121 |     datasource,
235.3     122 |   } = chartProps;
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Treemap/transformProps.ts:120:5
235.3 TS2339: Property 'emitCrossFilters' does not exist on type 'EchartsTreemapChartProps'.
235.3     118 |     theme,
235.3     119 |     inContextMenu,
235.3   > 120 |     emitCrossFilters,
235.3         |     ^^^^^^^^^^^^^^^^
235.3     121 |     datasource,
235.3     122 |   } = chartProps;
235.3     123 |   const { data = [] } = queriesData[0];
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Treemap/transformProps.ts:121:5
235.3 TS2339: Property 'datasource' does not exist on type 'EchartsTreemapChartProps'.
235.3     119 |     inContextMenu,
235.3     120 |     emitCrossFilters,
235.3   > 121 |     datasource,
235.3         |     ^^^^^^^^^^
235.3     122 |   } = chartProps;
235.3     123 |   const { data = [] } = queriesData[0];
235.3     124 |   const { columnFormats = {}, currencyFormats = {} } = datasource;
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Treemap/types.ts:20:8
235.3 TS1141: String literal expected.
235.3     18 |  */
235.3     19 | import {
235.3   > 20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3        |        ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     21 |   ChartDataResponseResult,
235.3     22 |   ChartProps,
235.3     23 |   QueryFormColumn,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Treemap/types.ts:20:118
235.3 TS2304: Cannot find name 'from'.
235.3     18 |  */
235.3     19 | import {
235.3   > 20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3        |                                                                                                                      ^^^^
235.3     21 |   ChartDataResponseResult,
235.3     22 |   ChartProps,
235.3     23 |   QueryFormColumn,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Treemap/types.ts:21:3
235.3 TS2304: Cannot find name 'ChartDataResponseResult'.
235.3     19 | import {
235.3     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 21 |   ChartDataResponseResult,
235.3        |   ^^^^^^^^^^^^^^^^^^^^^^^
235.3     22 |   ChartProps,
235.3     23 |   QueryFormColumn,
235.3     24 |   QueryFormData,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Treemap/types.ts:21:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     19 | import {
235.3     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 21 |   ChartDataResponseResult,
235.3        |   ^^^^^^^^^^^^^^^^^^^^^^^
235.3     22 |   ChartProps,
235.3     23 |   QueryFormColumn,
235.3     24 |   QueryFormData,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Treemap/types.ts:21:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     19 | import {
235.3     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 21 |   ChartDataResponseResult,
235.3        |   ^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 22 |   ChartProps,
235.3        | ^^^^^^^^^^^^^
235.3     23 |   QueryFormColumn,
235.3     24 |   QueryFormData,
235.3     25 |   QueryFormMetric,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Treemap/types.ts:21:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     19 | import {
235.3     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 21 |   ChartDataResponseResult,
235.3        |   ^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 22 |   ChartProps,
235.3        | ^^^^^^^^^^^^^
235.3   > 23 |   QueryFormColumn,
235.3        | ^^^^^^^^^^^^^^^^^^
235.3     24 |   QueryFormData,
235.3     25 |   QueryFormMetric,
235.3     26 | } from '@superset-ui/core';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Treemap/types.ts:21:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     19 | import {
235.3     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 21 |   ChartDataResponseResult,
235.3        |   ^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 22 |   ChartProps,
235.3        | ^^^^^^^^^^^^^
235.3   > 23 |   QueryFormColumn,
235.3        | ^^^^^^^^^^^^^
235.3   > 24 |   QueryFormData,
235.3        | ^^^^^^^^^^^^^^^^
235.3     25 |   QueryFormMetric,
235.3     26 | } from '@superset-ui/core';
235.3     27 | import type { CallbackDataParams } from 'echarts/types/src/util/types';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Treemap/types.ts:21:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     19 | import {
235.3     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 21 |   ChartDataResponseResult,
235.3        |   ^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 22 |   ChartProps,
235.3        | ^^^^^^^^^^^^^
235.3   > 23 |   QueryFormColumn,
235.3        | ^^^^^^^^^^^^^
235.3   > 24 |   QueryFormData,
235.3        | ^^^^^^^^^^^^^
235.3   > 25 |   QueryFormMetric,
235.3        | ^^^^^^^^^^^^^^^^^^
235.3     26 | } from '@superset-ui/core';
235.3     27 | import type { CallbackDataParams } from 'echarts/types/src/util/types';
235.3     28 | import {
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Treemap/types.ts:22:3
235.3 TS2304: Cannot find name 'ChartProps'.
235.3     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3     21 |   ChartDataResponseResult,
235.3   > 22 |   ChartProps,
235.3        |   ^^^^^^^^^^
235.3     23 |   QueryFormColumn,
235.3     24 |   QueryFormData,
235.3     25 |   QueryFormMetric,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Treemap/types.ts:23:3
235.3 TS2304: Cannot find name 'QueryFormColumn'.
235.3     21 |   ChartDataResponseResult,
235.3     22 |   ChartProps,
235.3   > 23 |   QueryFormColumn,
235.3        |   ^^^^^^^^^^^^^^^
235.3     24 |   QueryFormData,
235.3     25 |   QueryFormMetric,
235.3     26 | } from '@superset-ui/core';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Treemap/types.ts:24:3
235.3 TS2304: Cannot find name 'QueryFormData'.
235.3     22 |   ChartProps,
235.3     23 |   QueryFormColumn,
235.3   > 24 |   QueryFormData,
235.3        |   ^^^^^^^^^^^^^
235.3     25 |   QueryFormMetric,
235.3     26 | } from '@superset-ui/core';
235.3     27 | import type { CallbackDataParams } from 'echarts/types/src/util/types';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Treemap/types.ts:25:3
235.3 TS2304: Cannot find name 'QueryFormMetric'.
235.3     23 |   QueryFormColumn,
235.3     24 |   QueryFormData,
235.3   > 25 |   QueryFormMetric,
235.3        |   ^^^^^^^^^^^^^^^
235.3     26 | } from '@superset-ui/core';
235.3     27 | import type { CallbackDataParams } from 'echarts/types/src/util/types';
235.3     28 | import {
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Treemap/types.ts:26:3
235.3 TS2304: Cannot find name 'from'.
235.3     24 |   QueryFormData,
235.3     25 |   QueryFormMetric,
235.3   > 26 | } from '@superset-ui/core';
235.3        |   ^^^^
235.3     27 | import type { CallbackDataParams } from 'echarts/types/src/util/types';
235.3     28 | import {
235.3     29 |   BaseTransformedProps,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Treemap/types.ts:36:38
235.3 TS2304: Cannot find name 'QueryFormData'.
235.3     34 | } from '../types';
235.3     35 |
235.3   > 36 | export type EchartsTreemapFormData = QueryFormData & {
235.3        |                                      ^^^^^^^^^^^^^
235.3     37 |   colorScheme?: string;
235.3     38 |   groupby: QueryFormColumn[];
235.3     39 |   metric?: QueryFormMetric;
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Treemap/types.ts:38:12
235.3 TS2304: Cannot find name 'QueryFormColumn'.
235.3     36 | export type EchartsTreemapFormData = QueryFormData & {
235.3     37 |   colorScheme?: string;
235.3   > 38 |   groupby: QueryFormColumn[];
235.3        |            ^^^^^^^^^^^^^^^
235.3     39 |   metric?: QueryFormMetric;
235.3     40 |   labelType: EchartsTreemapLabelType;
235.3     41 |   labelPosition: LabelPositionEnum;
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Treemap/types.ts:39:12
235.3 TS2304: Cannot find name 'QueryFormMetric'.
235.3     37 |   colorScheme?: string;
235.3     38 |   groupby: QueryFormColumn[];
235.3   > 39 |   metric?: QueryFormMetric;
235.3        |            ^^^^^^^^^^^^^^^
235.3     40 |   labelType: EchartsTreemapLabelType;
235.3     41 |   labelPosition: LabelPositionEnum;
235.3     42 |   showLabels: boolean;
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Treemap/types.ts:56:11
235.3 TS2304: Cannot find name 'ChartProps'.
235.3     54 |
235.3     55 | export interface EchartsTreemapChartProps
235.3   > 56 |   extends ChartProps<EchartsTreemapFormData> {
235.3        |           ^^^^^^^^^^
235.3     57 |   formData: EchartsTreemapFormData;
235.3     58 |   queriesData: ChartDataResponseResult[];
235.3     59 | }
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/Treemap/types.ts:58:16
235.3 TS2304: Cannot find name 'ChartDataResponseResult'.
235.3     56 |   extends ChartProps<EchartsTreemapFormData> {
235.3     57 |   formData: EchartsTreemapFormData;
235.3   > 58 |   queriesData: ChartDataResponseResult[];
235.3        |                ^^^^^^^^^^^^^^^^^^^^^^^
235.3     59 | }
235.3     60 |
235.3     61 | export const DEFAULT_FORM_DATA: Partial<EchartsTreemapFormData> = {
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/types.ts:20:59
235.3 TS2300: Duplicate identifier 'QueryFormColumn'.
235.3     18 |  */
235.3     19 | import { RefObject, Ref } from 'react';
235.3   > 20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3        |                                                           ^^^^^^^^^^^^^^^
235.3     21 |
235.3     22 | import {
235.3     23 |   ChartDataResponseResult,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/types.ts:20:123
235.3 TS2307: Cannot find module '../types/local-compat' or its corresponding type declarations.
235.3     18 |  */
235.3     19 | import { RefObject, Ref } from 'react';
235.3   > 20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3        |                                                                                                                           ^^^^^^^^^^^^^^^^^^^^^^^
235.3     21 |
235.3     22 | import {
235.3     23 |   ChartDataResponseResult,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/types.ts:30:3
235.3 TS2300: Duplicate identifier 'QueryFormColumn'.
235.3     28 |   LegendState,
235.3     29 |   PlainObject,
235.3   > 30 |   QueryFormColumn,
235.3        |   ^^^^^^^^^^^^^^^
235.3     31 |   SetDataMaskHook,
235.3     32 |   ChartPlugin,
235.3     33 |   SqlaFormData,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/annotation.ts:32:3
235.3 TS2724: '"@superset-ui/core"' has no exported member named 'isRecordAnnotationResult'. Did you mean 'AnnotationResult'?
235.3     30 |   evalExpression,
235.3     31 |   FormulaAnnotationLayer,
235.3   > 32 |   isRecordAnnotationResult,
235.3        |   ^^^^^^^^^^^^^^^^^^^^^^^^
235.3     33 |   isTableAnnotationLayer,
235.3     34 |   isTimeseriesAnnotationResult,
235.3     35 | } from '@superset-ui/core';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/annotation.ts:34:3
235.3 TS2724: '"@superset-ui/core"' has no exported member named 'isTimeseriesAnnotationResult'. Did you mean 'isTimeseriesAnnotationLayer'?
235.3     32 |   isRecordAnnotationResult,
235.3     33 |   isTableAnnotationLayer,
235.3   > 34 |   isTimeseriesAnnotationResult,
235.3        |   ^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     35 | } from '@superset-ui/core';
235.3     36 | import { EchartsTimeseriesChartProps } from '../types';
235.3     37 | import { EchartsMixedTimeseriesProps } from '../MixedTimeseries/types';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/eventHandlers.ts:20:8
235.3 TS1141: String literal expected.
235.3     18 |  */
235.3     19 | import {
235.3   > 20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3        |        ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     21 |   BinaryQueryObjectFilterClause,
235.3     22 |   ContextMenuFilters,
235.3     23 |   DataMask,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/eventHandlers.ts:20:118
235.3 TS2304: Cannot find name 'from'.
235.3     18 |  */
235.3     19 | import {
235.3   > 20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3        |                                                                                                                      ^^^^
235.3     21 |   BinaryQueryObjectFilterClause,
235.3     22 |   ContextMenuFilters,
235.3     23 |   DataMask,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/eventHandlers.ts:21:3
235.3 TS2304: Cannot find name 'BinaryQueryObjectFilterClause'.
235.3     19 | import {
235.3     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 21 |   BinaryQueryObjectFilterClause,
235.3        |   ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     22 |   ContextMenuFilters,
235.3     23 |   DataMask,
235.3     24 |   QueryFormColumn,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/eventHandlers.ts:21:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     19 | import {
235.3     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 21 |   BinaryQueryObjectFilterClause,
235.3        |   ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     22 |   ContextMenuFilters,
235.3     23 |   DataMask,
235.3     24 |   QueryFormColumn,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/eventHandlers.ts:21:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     19 | import {
235.3     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 21 |   BinaryQueryObjectFilterClause,
235.3        |   ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 22 |   ContextMenuFilters,
235.3        | ^^^^^^^^^^^^^^^^^^^^^
235.3     23 |   DataMask,
235.3     24 |   QueryFormColumn,
235.3     25 |   QueryFormData,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/eventHandlers.ts:21:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     19 | import {
235.3     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 21 |   BinaryQueryObjectFilterClause,
235.3        |   ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 22 |   ContextMenuFilters,
235.3        | ^^^^^^^^^^^^^^^^^^^^^
235.3   > 23 |   DataMask,
235.3        | ^^^^^^^^^^^
235.3     24 |   QueryFormColumn,
235.3     25 |   QueryFormData,
235.3     26 |   getColumnLabel,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/eventHandlers.ts:21:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     19 | import {
235.3     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 21 |   BinaryQueryObjectFilterClause,
235.3        |   ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 22 |   ContextMenuFilters,
235.3        | ^^^^^^^^^^^^^^^^^^^^^
235.3   > 23 |   DataMask,
235.3        | ^^^^^^^^^^^^^^^^^^^^^
235.3   > 24 |   QueryFormColumn,
235.3        | ^^^^^^^^^^^^^^^^^^
235.3     25 |   QueryFormData,
235.3     26 |   getColumnLabel,
235.3     27 |   getNumberFormatter,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/eventHandlers.ts:21:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     19 | import {
235.3     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 21 |   BinaryQueryObjectFilterClause,
235.3        |   ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 22 |   ContextMenuFilters,
235.3        | ^^^^^^^^^^^^^^^^^^^^^
235.3   > 23 |   DataMask,
235.3        | ^^^^^^^^^^^^^^^^^^^^^
235.3   > 24 |   QueryFormColumn,
235.3        | ^^^^^^^^^^^^^^^^^^^^^
235.3   > 25 |   QueryFormData,
235.3        | ^^^^^^^^^^^^^^^^
235.3     26 |   getColumnLabel,
235.3     27 |   getNumberFormatter,
235.3     28 |   getTimeFormatter,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/eventHandlers.ts:21:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     19 | import {
235.3     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 21 |   BinaryQueryObjectFilterClause,
235.3        |   ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 22 |   ContextMenuFilters,
235.3        | ^^^^^^^^^^^^^^^^^^^^^
235.3   > 23 |   DataMask,
235.3        | ^^^^^^^^^^^^^^^^^^^^^
235.3   > 24 |   QueryFormColumn,
235.3        | ^^^^^^^^^^^^^^^^^^^^^
235.3   > 25 |   QueryFormData,
235.3        | ^^^^^^^^^^^^^^^^^^^^^
235.3   > 26 |   getColumnLabel,
235.3        | ^^^^^^^^^^^^^^^^^
235.3     27 |   getNumberFormatter,
235.3     28 |   getTimeFormatter,
235.3     29 | } from '@superset-ui/core';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/eventHandlers.ts:21:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     19 | import {
235.3     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 21 |   BinaryQueryObjectFilterClause,
235.3        |   ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 22 |   ContextMenuFilters,
235.3        | ^^^^^^^^^^^^^^^^^^^^^
235.3   > 23 |   DataMask,
235.3        | ^^^^^^^^^^^^^^^^^^^^^
235.3   > 24 |   QueryFormColumn,
235.3        | ^^^^^^^^^^^^^^^^^^^^^
235.3   > 25 |   QueryFormData,
235.3        | ^^^^^^^^^^^^^^^^^^^^^
235.3   > 26 |   getColumnLabel,
235.3        | ^^^^^^^^^^^^^^^^^^^^^
235.3   > 27 |   getNumberFormatter,
235.3        | ^^^^^^^^^^^^^^^^^^^^^
235.3     28 |   getTimeFormatter,
235.3     29 | } from '@superset-ui/core';
235.3     30 |
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/eventHandlers.ts:21:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     19 | import {
235.3     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 21 |   BinaryQueryObjectFilterClause,
235.3        |   ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 22 |   ContextMenuFilters,
235.3        | ^^^^^^^^^^^^^^^^^^^^^
235.3   > 23 |   DataMask,
235.3        | ^^^^^^^^^^^^^^^^^^^^^
235.3   > 24 |   QueryFormColumn,
235.3        | ^^^^^^^^^^^^^^^^^^^^^
235.3   > 25 |   QueryFormData,
235.3        | ^^^^^^^^^^^^^^^^^^^^^
235.3   > 26 |   getColumnLabel,
235.3        | ^^^^^^^^^^^^^^^^^^^^^
235.3   > 27 |   getNumberFormatter,
235.3        | ^^^^^^^^^^^^^^^^^^^^^
235.3   > 28 |   getTimeFormatter,
235.3        | ^^^^^^^^^^^^^^^^^^^
235.3     29 | } from '@superset-ui/core';
235.3     30 |
235.3     31 | import {
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/eventHandlers.ts:22:3
235.3 TS2304: Cannot find name 'ContextMenuFilters'.
235.3     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3     21 |   BinaryQueryObjectFilterClause,
235.3   > 22 |   ContextMenuFilters,
235.3        |   ^^^^^^^^^^^^^^^^^^
235.3     23 |   DataMask,
235.3     24 |   QueryFormColumn,
235.3     25 |   QueryFormData,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/eventHandlers.ts:23:3
235.3 TS2304: Cannot find name 'DataMask'.
235.3     21 |   BinaryQueryObjectFilterClause,
235.3     22 |   ContextMenuFilters,
235.3   > 23 |   DataMask,
235.3        |   ^^^^^^^^
235.3     24 |   QueryFormColumn,
235.3     25 |   QueryFormData,
235.3     26 |   getColumnLabel,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/eventHandlers.ts:24:3
235.3 TS2304: Cannot find name 'QueryFormColumn'.
235.3     22 |   ContextMenuFilters,
235.3     23 |   DataMask,
235.3   > 24 |   QueryFormColumn,
235.3        |   ^^^^^^^^^^^^^^^
235.3     25 |   QueryFormData,
235.3     26 |   getColumnLabel,
235.3     27 |   getNumberFormatter,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/eventHandlers.ts:25:3
235.3 TS2304: Cannot find name 'QueryFormData'.
235.3     23 |   DataMask,
235.3     24 |   QueryFormColumn,
235.3   > 25 |   QueryFormData,
235.3        |   ^^^^^^^^^^^^^
235.3     26 |   getColumnLabel,
235.3     27 |   getNumberFormatter,
235.3     28 |   getTimeFormatter,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/eventHandlers.ts:26:3
235.3 TS2304: Cannot find name 'getColumnLabel'.
235.3     24 |   QueryFormColumn,
235.3     25 |   QueryFormData,
235.3   > 26 |   getColumnLabel,
235.3        |   ^^^^^^^^^^^^^^
235.3     27 |   getNumberFormatter,
235.3     28 |   getTimeFormatter,
235.3     29 | } from '@superset-ui/core';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/eventHandlers.ts:27:3
235.3 TS2304: Cannot find name 'getNumberFormatter'.
235.3     25 |   QueryFormData,
235.3     26 |   getColumnLabel,
235.3   > 27 |   getNumberFormatter,
235.3        |   ^^^^^^^^^^^^^^^^^^
235.3     28 |   getTimeFormatter,
235.3     29 | } from '@superset-ui/core';
235.3     30 |
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/eventHandlers.ts:28:3
235.3 TS2304: Cannot find name 'getTimeFormatter'.
235.3     26 |   getColumnLabel,
235.3     27 |   getNumberFormatter,
235.3   > 28 |   getTimeFormatter,
235.3        |   ^^^^^^^^^^^^^^^^
235.3     29 | } from '@superset-ui/core';
235.3     30 |
235.3     31 | import {
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/eventHandlers.ts:29:3
235.3 TS2304: Cannot find name 'from'.
235.3     27 |   getNumberFormatter,
235.3     28 |   getTimeFormatter,
235.3   > 29 | } from '@superset-ui/core';
235.3        |   ^^^^
235.3     30 |
235.3     31 | import {
235.3     32 |   BaseTransformedProps,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/eventHandlers.ts:46:14
235.3 TS2304: Cannot find name 'QueryFormColumn'.
235.3     44 |   (
235.3     45 |     selectedValues: Record<number, string>,
235.3   > 46 |     groupby: QueryFormColumn[],
235.3        |              ^^^^^^^^^^^^^^^
235.3     47 |     labelMap: Record<string, string[]>,
235.3     48 |   ) =>
235.3     49 |   (value: string) => {
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/eventHandlers.ts:93:10
235.3 TS2304: Cannot find name 'ContextMenuFilters'.
235.3     91 |     getCrossFilterDataMask: (
235.3     92 |       value: string,
235.3   > 93 |     ) => ContextMenuFilters['crossFilter'],
235.3        |          ^^^^^^^^^^^^^^^^^^
235.3     94 |     setDataMask: (dataMask: DataMask) => void,
235.3     95 |     emitCrossFilters?: boolean,
235.3     96 |   ) =>
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/eventHandlers.ts:94:29
235.3 TS2304: Cannot find name 'DataMask'.
235.3     92 |       value: string,
235.3     93 |     ) => ContextMenuFilters['crossFilter'],
235.3   > 94 |     setDataMask: (dataMask: DataMask) => void,
235.3        |                             ^^^^^^^^
235.3     95 |     emitCrossFilters?: boolean,
235.3     96 |   ) =>
235.3     97 |   ({ name }: { name: string }) => {
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/eventHandlers.ts:115:10
235.3 TS2304: Cannot find name 'ContextMenuFilters'.
235.3     113 |     getCrossFilterDataMask: (
235.3     114 |       value: string,
235.3   > 115 |     ) => ContextMenuFilters['crossFilter'],
235.3         |          ^^^^^^^^^^^^^^^^^^
235.3     116 |     formData: QueryFormData,
235.3     117 |     coltypeMapping?: Record<string, number>,
235.3     118 |   ) =>
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/eventHandlers.ts:116:15
235.3 TS2304: Cannot find name 'QueryFormData'.
235.3     114 |       value: string,
235.3     115 |     ) => ContextMenuFilters['crossFilter'],
235.3   > 116 |     formData: QueryFormData,
235.3         |               ^^^^^^^^^^^^^
235.3     117 |     coltypeMapping?: Record<string, number>,
235.3     118 |   ) =>
235.3     119 |   (e: Event) => {
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/eventHandlers.ts:123:27
235.3 TS2304: Cannot find name 'BinaryQueryObjectFilterClause'.
235.3     121 |       e.event.stop();
235.3     122 |       const pointerEvent = e.event.event;
235.3   > 123 |       const drillFilters: BinaryQueryObjectFilterClause[] = [];
235.3         |                           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     124 |       if (groupby.length > 0) {
235.3     125 |         const values = labelMap[e.name];
235.3     126 |         groupby.forEach((dimension, i) => {
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/eventHandlers.ts:132:30
235.3 TS2304: Cannot find name 'getTimeFormatter'.
235.3     130 |             val: values[i],
235.3     131 |             formattedVal: formatSeriesName(values[i], {
235.3   > 132 |               timeFormatter: getTimeFormatter(formData.dateFormat),
235.3         |                              ^^^^^^^^^^^^^^^^
235.3     133 |               numberFormatter: getNumberFormatter(formData.numberFormat),
235.3     134 |               coltype: coltypeMapping?.[getColumnLabel(dimension)],
235.3     135 |             }),
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/eventHandlers.ts:133:32
235.3 TS2304: Cannot find name 'getNumberFormatter'.
235.3     131 |             formattedVal: formatSeriesName(values[i], {
235.3     132 |               timeFormatter: getTimeFormatter(formData.dateFormat),
235.3   > 133 |               numberFormatter: getNumberFormatter(formData.numberFormat),
235.3         |                                ^^^^^^^^^^^^^^^^^^
235.3     134 |               coltype: coltypeMapping?.[getColumnLabel(dimension)],
235.3     135 |             }),
235.3     136 |           });
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/eventHandlers.ts:134:41
235.3 TS2304: Cannot find name 'getColumnLabel'.
235.3     132 |               timeFormatter: getTimeFormatter(formData.dateFormat),
235.3     133 |               numberFormatter: getNumberFormatter(formData.numberFormat),
235.3   > 134 |               coltype: coltypeMapping?.[getColumnLabel(dimension)],
235.3         |                                         ^^^^^^^^^^^^^^
235.3     135 |             }),
235.3     136 |           });
235.3     137 |         });
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/formatters.ts:21:8
235.3 TS1141: String literal expected.
235.3     19 |
235.3     20 | import {
235.3   > 21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3        |        ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     22 |   CurrencyFormatter,
235.3     23 |   ensureIsArray,
235.3     24 |   getNumberFormatter,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/formatters.ts:21:118
235.3 TS2304: Cannot find name 'from'.
235.3     19 |
235.3     20 | import {
235.3   > 21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3        |                                                                                                                      ^^^^
235.3     22 |   CurrencyFormatter,
235.3     23 |   ensureIsArray,
235.3     24 |   getNumberFormatter,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/formatters.ts:22:3
235.3 TS2304: Cannot find name 'CurrencyFormatter'.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   CurrencyFormatter,
235.3        |   ^^^^^^^^^^^^^^^^^
235.3     23 |   ensureIsArray,
235.3     24 |   getNumberFormatter,
235.3     25 |   getTimeFormatter,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/formatters.ts:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   CurrencyFormatter,
235.3        |   ^^^^^^^^^^^^^^^^^
235.3     23 |   ensureIsArray,
235.3     24 |   getNumberFormatter,
235.3     25 |   getTimeFormatter,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/formatters.ts:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   CurrencyFormatter,
235.3        |   ^^^^^^^^^^^^^^^^^^
235.3   > 23 |   ensureIsArray,
235.3        | ^^^^^^^^^^^^^^^^
235.3     24 |   getNumberFormatter,
235.3     25 |   getTimeFormatter,
235.3     26 |   isSavedMetric,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/formatters.ts:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   CurrencyFormatter,
235.3        |   ^^^^^^^^^^^^^^^^^^
235.3   > 23 |   ensureIsArray,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 24 |   getNumberFormatter,
235.3        | ^^^^^^^^^^^^^^^^^^^^^
235.3     25 |   getTimeFormatter,
235.3     26 |   isSavedMetric,
235.3     27 |   NumberFormats,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/formatters.ts:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   CurrencyFormatter,
235.3        |   ^^^^^^^^^^^^^^^^^^
235.3   > 23 |   ensureIsArray,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 24 |   getNumberFormatter,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 25 |   getTimeFormatter,
235.3        | ^^^^^^^^^^^^^^^^^^^
235.3     26 |   isSavedMetric,
235.3     27 |   NumberFormats,
235.3     28 |   QueryFormMetric,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/formatters.ts:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   CurrencyFormatter,
235.3        |   ^^^^^^^^^^^^^^^^^^
235.3   > 23 |   ensureIsArray,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 24 |   getNumberFormatter,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 25 |   getTimeFormatter,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 26 |   isSavedMetric,
235.3        | ^^^^^^^^^^^^^^^^
235.3     27 |   NumberFormats,
235.3     28 |   QueryFormMetric,
235.3     29 |   SMART_DATE_DETAILED_ID,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/formatters.ts:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   CurrencyFormatter,
235.3        |   ^^^^^^^^^^^^^^^^^^
235.3   > 23 |   ensureIsArray,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 24 |   getNumberFormatter,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 25 |   getTimeFormatter,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 26 |   isSavedMetric,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 27 |   NumberFormats,
235.3        | ^^^^^^^^^^^^^^^^
235.3     28 |   QueryFormMetric,
235.3     29 |   SMART_DATE_DETAILED_ID,
235.3     30 |   SMART_DATE_ID,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/formatters.ts:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   CurrencyFormatter,
235.3        |   ^^^^^^^^^^^^^^^^^^
235.3   > 23 |   ensureIsArray,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 24 |   getNumberFormatter,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 25 |   getTimeFormatter,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 26 |   isSavedMetric,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 27 |   NumberFormats,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 28 |   QueryFormMetric,
235.3        | ^^^^^^^^^^^^^^^^^^
235.3     29 |   SMART_DATE_DETAILED_ID,
235.3     30 |   SMART_DATE_ID,
235.3     31 |   SMART_DATE_VERBOSE_ID,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/formatters.ts:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   CurrencyFormatter,
235.3        |   ^^^^^^^^^^^^^^^^^^
235.3   > 23 |   ensureIsArray,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 24 |   getNumberFormatter,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 25 |   getTimeFormatter,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 26 |   isSavedMetric,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 27 |   NumberFormats,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 28 |   QueryFormMetric,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 29 |   SMART_DATE_DETAILED_ID,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     30 |   SMART_DATE_ID,
235.3     31 |   SMART_DATE_VERBOSE_ID,
235.3     32 |   TimeFormatter,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/formatters.ts:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   CurrencyFormatter,
235.3        |   ^^^^^^^^^^^^^^^^^^
235.3   > 23 |   ensureIsArray,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 24 |   getNumberFormatter,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 25 |   getTimeFormatter,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 26 |   isSavedMetric,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 27 |   NumberFormats,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 28 |   QueryFormMetric,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 29 |   SMART_DATE_DETAILED_ID,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 30 |   SMART_DATE_ID,
235.3        | ^^^^^^^^^^^^^^^^
235.3     31 |   SMART_DATE_VERBOSE_ID,
235.3     32 |   TimeFormatter,
235.3     33 |   ValueFormatter,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/formatters.ts:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   CurrencyFormatter,
235.3        |   ^^^^^^^^^^^^^^^^^^
235.3   > 23 |   ensureIsArray,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 24 |   getNumberFormatter,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 25 |   getTimeFormatter,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 26 |   isSavedMetric,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 27 |   NumberFormats,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 28 |   QueryFormMetric,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 29 |   SMART_DATE_DETAILED_ID,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 30 |   SMART_DATE_ID,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 31 |   SMART_DATE_VERBOSE_ID,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^
235.3     32 |   TimeFormatter,
235.3     33 |   ValueFormatter,
235.3     34 | } from '@superset-ui/core';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/formatters.ts:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   CurrencyFormatter,
235.3        |   ^^^^^^^^^^^^^^^^^^
235.3   > 23 |   ensureIsArray,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 24 |   getNumberFormatter,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 25 |   getTimeFormatter,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 26 |   isSavedMetric,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 27 |   NumberFormats,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 28 |   QueryFormMetric,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 29 |   SMART_DATE_DETAILED_ID,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 30 |   SMART_DATE_ID,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 31 |   SMART_DATE_VERBOSE_ID,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 32 |   TimeFormatter,
235.3        | ^^^^^^^^^^^^^^^^
235.3     33 |   ValueFormatter,
235.3     34 | } from '@superset-ui/core';
235.3     35 |
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/formatters.ts:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   CurrencyFormatter,
235.3        |   ^^^^^^^^^^^^^^^^^^
235.3   > 23 |   ensureIsArray,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 24 |   getNumberFormatter,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 25 |   getTimeFormatter,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 26 |   isSavedMetric,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 27 |   NumberFormats,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 28 |   QueryFormMetric,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 29 |   SMART_DATE_DETAILED_ID,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 30 |   SMART_DATE_ID,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 31 |   SMART_DATE_VERBOSE_ID,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 32 |   TimeFormatter,
235.3        | ^^^^^^^^^^^^^^^^
235.3   > 33 |   ValueFormatter,
235.3        | ^^^^^^^^^^^^^^^^^
235.3     34 | } from '@superset-ui/core';
235.3     35 |
235.3     36 | export const getSmartDateDetailedFormatter = () =>
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/formatters.ts:23:3
235.3 TS2304: Cannot find name 'ensureIsArray'.
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3     22 |   CurrencyFormatter,
235.3   > 23 |   ensureIsArray,
235.3        |   ^^^^^^^^^^^^^
235.3     24 |   getNumberFormatter,
235.3     25 |   getTimeFormatter,
235.3     26 |   isSavedMetric,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/formatters.ts:24:3
235.3 TS2304: Cannot find name 'getNumberFormatter'.
235.3     22 |   CurrencyFormatter,
235.3     23 |   ensureIsArray,
235.3   > 24 |   getNumberFormatter,
235.3        |   ^^^^^^^^^^^^^^^^^^
235.3     25 |   getTimeFormatter,
235.3     26 |   isSavedMetric,
235.3     27 |   NumberFormats,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/formatters.ts:25:3
235.3 TS2304: Cannot find name 'getTimeFormatter'.
235.3     23 |   ensureIsArray,
235.3     24 |   getNumberFormatter,
235.3   > 25 |   getTimeFormatter,
235.3        |   ^^^^^^^^^^^^^^^^
235.3     26 |   isSavedMetric,
235.3     27 |   NumberFormats,
235.3     28 |   QueryFormMetric,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/formatters.ts:26:3
235.3 TS2304: Cannot find name 'isSavedMetric'.
235.3     24 |   getNumberFormatter,
235.3     25 |   getTimeFormatter,
235.3   > 26 |   isSavedMetric,
235.3        |   ^^^^^^^^^^^^^
235.3     27 |   NumberFormats,
235.3     28 |   QueryFormMetric,
235.3     29 |   SMART_DATE_DETAILED_ID,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/formatters.ts:27:3
235.3 TS2304: Cannot find name 'NumberFormats'.
235.3     25 |   getTimeFormatter,
235.3     26 |   isSavedMetric,
235.3   > 27 |   NumberFormats,
235.3        |   ^^^^^^^^^^^^^
235.3     28 |   QueryFormMetric,
235.3     29 |   SMART_DATE_DETAILED_ID,
235.3     30 |   SMART_DATE_ID,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/formatters.ts:28:3
235.3 TS2304: Cannot find name 'QueryFormMetric'.
235.3     26 |   isSavedMetric,
235.3     27 |   NumberFormats,
235.3   > 28 |   QueryFormMetric,
235.3        |   ^^^^^^^^^^^^^^^
235.3     29 |   SMART_DATE_DETAILED_ID,
235.3     30 |   SMART_DATE_ID,
235.3     31 |   SMART_DATE_VERBOSE_ID,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/formatters.ts:29:3
235.3 TS2304: Cannot find name 'SMART_DATE_DETAILED_ID'.
235.3     27 |   NumberFormats,
235.3     28 |   QueryFormMetric,
235.3   > 29 |   SMART_DATE_DETAILED_ID,
235.3        |   ^^^^^^^^^^^^^^^^^^^^^^
235.3     30 |   SMART_DATE_ID,
235.3     31 |   SMART_DATE_VERBOSE_ID,
235.3     32 |   TimeFormatter,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/formatters.ts:30:3
235.3 TS2304: Cannot find name 'SMART_DATE_ID'.
235.3     28 |   QueryFormMetric,
235.3     29 |   SMART_DATE_DETAILED_ID,
235.3   > 30 |   SMART_DATE_ID,
235.3        |   ^^^^^^^^^^^^^
235.3     31 |   SMART_DATE_VERBOSE_ID,
235.3     32 |   TimeFormatter,
235.3     33 |   ValueFormatter,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/formatters.ts:31:3
235.3 TS2304: Cannot find name 'SMART_DATE_VERBOSE_ID'.
235.3     29 |   SMART_DATE_DETAILED_ID,
235.3     30 |   SMART_DATE_ID,
235.3   > 31 |   SMART_DATE_VERBOSE_ID,
235.3        |   ^^^^^^^^^^^^^^^^^^^^^
235.3     32 |   TimeFormatter,
235.3     33 |   ValueFormatter,
235.3     34 | } from '@superset-ui/core';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/formatters.ts:32:3
235.3 TS2304: Cannot find name 'TimeFormatter'.
235.3     30 |   SMART_DATE_ID,
235.3     31 |   SMART_DATE_VERBOSE_ID,
235.3   > 32 |   TimeFormatter,
235.3        |   ^^^^^^^^^^^^^
235.3     33 |   ValueFormatter,
235.3     34 | } from '@superset-ui/core';
235.3     35 |
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/formatters.ts:33:3
235.3 TS2304: Cannot find name 'ValueFormatter'.
235.3     31 |   SMART_DATE_VERBOSE_ID,
235.3     32 |   TimeFormatter,
235.3   > 33 |   ValueFormatter,
235.3        |   ^^^^^^^^^^^^^^
235.3     34 | } from '@superset-ui/core';
235.3     35 |
235.3     36 | export const getSmartDateDetailedFormatter = () =>
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/formatters.ts:34:3
235.3 TS2304: Cannot find name 'from'.
235.3     32 |   TimeFormatter,
235.3     33 |   ValueFormatter,
235.3   > 34 | } from '@superset-ui/core';
235.3        |   ^^^^
235.3     35 |
235.3     36 | export const getSmartDateDetailedFormatter = () =>
235.3     37 |   getTimeFormatter(SMART_DATE_DETAILED_ID);
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/formatters.ts:37:3
235.3 TS2304: Cannot find name 'getTimeFormatter'.
235.3     35 |
235.3     36 | export const getSmartDateDetailedFormatter = () =>
235.3   > 37 |   getTimeFormatter(SMART_DATE_DETAILED_ID);
235.3        |   ^^^^^^^^^^^^^^^^
235.3     38 |
235.3     39 | export const getSmartDateFormatter = () => getTimeFormatter(SMART_DATE_ID);
235.3     40 |
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/formatters.ts:37:20
235.3 TS2304: Cannot find name 'SMART_DATE_DETAILED_ID'.
235.3     35 |
235.3     36 | export const getSmartDateDetailedFormatter = () =>
235.3   > 37 |   getTimeFormatter(SMART_DATE_DETAILED_ID);
235.3        |                    ^^^^^^^^^^^^^^^^^^^^^^
235.3     38 |
235.3     39 | export const getSmartDateFormatter = () => getTimeFormatter(SMART_DATE_ID);
235.3     40 |
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/formatters.ts:39:44
235.3 TS2304: Cannot find name 'getTimeFormatter'.
235.3     37 |   getTimeFormatter(SMART_DATE_DETAILED_ID);
235.3     38 |
235.3   > 39 | export const getSmartDateFormatter = () => getTimeFormatter(SMART_DATE_ID);
235.3        |                                            ^^^^^^^^^^^^^^^^
235.3     40 |
235.3     41 | export const getSmartDateVerboseFormatter = () =>
235.3     42 |   getTimeFormatter(SMART_DATE_VERBOSE_ID);
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/formatters.ts:39:61
235.3 TS2304: Cannot find name 'SMART_DATE_ID'.
235.3     37 |   getTimeFormatter(SMART_DATE_DETAILED_ID);
235.3     38 |
235.3   > 39 | export const getSmartDateFormatter = () => getTimeFormatter(SMART_DATE_ID);
235.3        |                                                             ^^^^^^^^^^^^^
235.3     40 |
235.3     41 | export const getSmartDateVerboseFormatter = () =>
235.3     42 |   getTimeFormatter(SMART_DATE_VERBOSE_ID);
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/formatters.ts:42:3
235.3 TS2304: Cannot find name 'getTimeFormatter'.
235.3     40 |
235.3     41 | export const getSmartDateVerboseFormatter = () =>
235.3   > 42 |   getTimeFormatter(SMART_DATE_VERBOSE_ID);
235.3        |   ^^^^^^^^^^^^^^^^
235.3     43 |
235.3     44 | export const getPercentFormatter = (format?: string) =>
235.3     45 |   getNumberFormatter(
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/formatters.ts:42:20
235.3 TS2304: Cannot find name 'SMART_DATE_VERBOSE_ID'.
235.3     40 |
235.3     41 | export const getSmartDateVerboseFormatter = () =>
235.3   > 42 |   getTimeFormatter(SMART_DATE_VERBOSE_ID);
235.3        |                    ^^^^^^^^^^^^^^^^^^^^^
235.3     43 |
235.3     44 | export const getPercentFormatter = (format?: string) =>
235.3     45 |   getNumberFormatter(
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/formatters.ts:45:3
235.3 TS2304: Cannot find name 'getNumberFormatter'.
235.3     43 |
235.3     44 | export const getPercentFormatter = (format?: string) =>
235.3   > 45 |   getNumberFormatter(
235.3        |   ^^^^^^^^^^^^^^^^^^
235.3     46 |     !format || format === NumberFormats.SMART_NUMBER
235.3     47 |       ? NumberFormats.PERCENT
235.3     48 |       : format,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/formatters.ts:46:27
235.3 TS2304: Cannot find name 'NumberFormats'.
235.3     44 | export const getPercentFormatter = (format?: string) =>
235.3     45 |   getNumberFormatter(
235.3   > 46 |     !format || format === NumberFormats.SMART_NUMBER
235.3        |                           ^^^^^^^^^^^^^
235.3     47 |       ? NumberFormats.PERCENT
235.3     48 |       : format,
235.3     49 |   );
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/formatters.ts:47:9
235.3 TS2304: Cannot find name 'NumberFormats'.
235.3     45 |   getNumberFormatter(
235.3     46 |     !format || format === NumberFormats.SMART_NUMBER
235.3   > 47 |       ? NumberFormats.PERCENT
235.3        |         ^^^^^^^^^^^^^
235.3     48 |       : format,
235.3     49 |   );
235.3     50 |
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/formatters.ts:52:12
235.3 TS2304: Cannot find name 'QueryFormMetric'.
235.3     50 |
235.3     51 | export const getYAxisFormatter = (
235.3   > 52 |   metrics: QueryFormMetric[],
235.3        |            ^^^^^^^^^^^^^^^
235.3     53 |   forcePercentFormatter: boolean,
235.3     54 |   customFormatters: Record<string, ValueFormatter>,
235.3     55 |   defaultFormatter: ValueFormatter,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/formatters.ts:54:36
235.3 TS2304: Cannot find name 'ValueFormatter'.
235.3     52 |   metrics: QueryFormMetric[],
235.3     53 |   forcePercentFormatter: boolean,
235.3   > 54 |   customFormatters: Record<string, ValueFormatter>,
235.3        |                                    ^^^^^^^^^^^^^^
235.3     55 |   defaultFormatter: ValueFormatter,
235.3     56 |   format?: string,
235.3     57 | ) => {
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/formatters.ts:55:21
235.3 TS2304: Cannot find name 'ValueFormatter'.
235.3     53 |   forcePercentFormatter: boolean,
235.3     54 |   customFormatters: Record<string, ValueFormatter>,
235.3   > 55 |   defaultFormatter: ValueFormatter,
235.3        |                     ^^^^^^^^^^^^^^
235.3     56 |   format?: string,
235.3     57 | ) => {
235.3     58 |   if (forcePercentFormatter) {
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/formatters.ts:61:24
235.3 TS2304: Cannot find name 'ensureIsArray'.
235.3     59 |     return getPercentFormatter(format);
235.3     60 |   }
235.3   > 61 |   const metricsArray = ensureIsArray(metrics);
235.3        |                        ^^^^^^^^^^^^^
235.3     62 |   if (
235.3     63 |     metricsArray.every(isSavedMetric) &&
235.3     64 |     metricsArray
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/formatters.ts:63:24
235.3 TS2304: Cannot find name 'isSavedMetric'.
235.3     61 |   const metricsArray = ensureIsArray(metrics);
235.3     62 |   if (
235.3   > 63 |     metricsArray.every(isSavedMetric) &&
235.3        |                        ^^^^^^^^^^^^^
235.3     64 |     metricsArray
235.3     65 |       .map(metric => customFormatters[metric])
235.3     66 |       .every(
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/formatters.ts:68:32
235.3 TS2304: Cannot find name 'CurrencyFormatter'.
235.3     66 |       .every(
235.3     67 |         (formatter, _, formatters) =>
235.3   > 68 |           formatter instanceof CurrencyFormatter &&
235.3        |                                ^^^^^^^^^^^^^^^^^
235.3     69 |           (formatter as CurrencyFormatter)?.currency?.symbol ===
235.3     70 |             (formatters[0] as CurrencyFormatter)?.currency?.symbol,
235.3     71 |       )
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/formatters.ts:69:25
235.3 TS2304: Cannot find name 'CurrencyFormatter'.
235.3     67 |         (formatter, _, formatters) =>
235.3     68 |           formatter instanceof CurrencyFormatter &&
235.3   > 69 |           (formatter as CurrencyFormatter)?.currency?.symbol ===
235.3        |                         ^^^^^^^^^^^^^^^^^
235.3     70 |             (formatters[0] as CurrencyFormatter)?.currency?.symbol,
235.3     71 |       )
235.3     72 |   ) {
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/formatters.ts:70:31
235.3 TS2304: Cannot find name 'CurrencyFormatter'.
235.3     68 |           formatter instanceof CurrencyFormatter &&
235.3     69 |           (formatter as CurrencyFormatter)?.currency?.symbol ===
235.3   > 70 |             (formatters[0] as CurrencyFormatter)?.currency?.symbol,
235.3        |                               ^^^^^^^^^^^^^^^^^
235.3     71 |       )
235.3     72 |   ) {
235.3     73 |     return customFormatters[metricsArray[0]];
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/formatters.ts:75:30
235.3 TS2304: Cannot find name 'getNumberFormatter'.
235.3     73 |     return customFormatters[metricsArray[0]];
235.3     74 |   }
235.3   > 75 |   return defaultFormatter ?? getNumberFormatter();
235.3        |                              ^^^^^^^^^^^^^^^^^^
235.3     76 | };
235.3     77 |
235.3     78 | export function getTooltipTimeFormatter(
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/formatters.ts:80:4
235.3 TS2304: Cannot find name 'TimeFormatter'.
235.3     78 | export function getTooltipTimeFormatter(
235.3     79 |   format?: string,
235.3   > 80 | ): TimeFormatter | StringConstructor {
235.3        |    ^^^^^^^^^^^^^
235.3     81 |   if (format === SMART_DATE_ID) {
235.3     82 |     return getSmartDateVerboseFormatter();
235.3     83 |   }
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/formatters.ts:81:18
235.3 TS2304: Cannot find name 'SMART_DATE_ID'.
235.3     79 |   format?: string,
235.3     80 | ): TimeFormatter | StringConstructor {
235.3   > 81 |   if (format === SMART_DATE_ID) {
235.3        |                  ^^^^^^^^^^^^^
235.3     82 |     return getSmartDateVerboseFormatter();
235.3     83 |   }
235.3     84 |   if (format) {
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/formatters.ts:85:12
235.3 TS2304: Cannot find name 'getTimeFormatter'.
235.3     83 |   }
235.3     84 |   if (format) {
235.3   > 85 |     return getTimeFormatter(format);
235.3        |            ^^^^^^^^^^^^^^^^
235.3     86 |   }
235.3     87 |   return String;
235.3     88 | }
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/formatters.ts:92:4
235.3 TS2304: Cannot find name 'TimeFormatter'.
235.3     90 | export function getXAxisFormatter(
235.3     91 |   format?: string,
235.3   > 92 | ): TimeFormatter | StringConstructor | undefined {
235.3        |    ^^^^^^^^^^^^^
235.3     93 |   if (format === SMART_DATE_ID || !format) {
235.3     94 |     return undefined;
235.3     95 |   }
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/formatters.ts:93:18
235.3 TS2304: Cannot find name 'SMART_DATE_ID'.
235.3     91 |   format?: string,
235.3     92 | ): TimeFormatter | StringConstructor | undefined {
235.3   > 93 |   if (format === SMART_DATE_ID || !format) {
235.3        |                  ^^^^^^^^^^^^^
235.3     94 |     return undefined;
235.3     95 |   }
235.3     96 |   if (format) {
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/formatters.ts:97:12
235.3 TS2304: Cannot find name 'getTimeFormatter'.
235.3      95 |   }
235.3      96 |   if (format) {
235.3   >  97 |     return getTimeFormatter(format);
235.3         |            ^^^^^^^^^^^^^^^^
235.3      98 |   }
235.3      99 |   return String;
235.3     100 | }
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/formDataSuffix.ts:19:10
235.3 TS2300: Duplicate identifier 'QueryFormData'.
235.3     17 |  * under the License.
235.3     18 |  */
235.3   > 19 | import { QueryFormData } from '@superset-ui/core';
235.3        |          ^^^^^^^^^^^^^
235.3     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3     21 |
235.3     22 | export const retainFormDataSuffix = (
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/formDataSuffix.ts:20:27
235.3 TS2300: Duplicate identifier 'QueryFormData'.
235.3     18 |  */
235.3     19 | import { QueryFormData } from '@superset-ui/core';
235.3   > 20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3        |                           ^^^^^^^^^^^^^
235.3     21 |
235.3     22 | export const retainFormDataSuffix = (
235.3     23 |   formData: QueryFormData,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/metricDisplayName.ts:20:10
235.3 TS2300: Duplicate identifier 'QueryFormMetric'.
235.3     18 |  */
235.3     19 |
235.3   > 20 | import { QueryFormMetric } from '@superset-ui/core';
235.3        |          ^^^^^^^^^^^^^^^
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3     22 |
235.3     23 | export const getMetricDisplayName = (
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/metricDisplayName.ts:21:42
235.3 TS2300: Duplicate identifier 'QueryFormMetric'.
235.3     19 |
235.3     20 | import { QueryFormMetric } from '@superset-ui/core';
235.3   > 21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3        |                                          ^^^^^^^^^^^^^^^
235.3     22 |
235.3     23 | export const getMetricDisplayName = (
235.3     24 |   metric: QueryFormMetric,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:21:8
235.3 TS1141: String literal expected.
235.3     19 |  */
235.3     20 | import {
235.3   > 21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3        |        ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     22 |   AxisType,
235.3     23 |   ChartDataResponseResult,
235.3     24 |   DataRecord,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:21:118
235.3 TS2304: Cannot find name 'from'.
235.3     19 |  */
235.3     20 | import {
235.3   > 21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3        |                                                                                                                      ^^^^
235.3     22 |   AxisType,
235.3     23 |   ChartDataResponseResult,
235.3     24 |   DataRecord,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:22:3
235.3 TS2304: Cannot find name 'AxisType'.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   AxisType,
235.3        |   ^^^^^^^^
235.3     23 |   ChartDataResponseResult,
235.3     24 |   DataRecord,
235.3     25 |   DataRecordValue,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   AxisType,
235.3        |   ^^^^^^^^
235.3     23 |   ChartDataResponseResult,
235.3     24 |   DataRecord,
235.3     25 |   DataRecordValue,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   AxisType,
235.3        |   ^^^^^^^^^
235.3   > 23 |   ChartDataResponseResult,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3     24 |   DataRecord,
235.3     25 |   DataRecordValue,
235.3     26 |   DTTM_ALIAS,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   AxisType,
235.3        |   ^^^^^^^^^
235.3   > 23 |   ChartDataResponseResult,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 24 |   DataRecord,
235.3        | ^^^^^^^^^^^^^
235.3     25 |   DataRecordValue,
235.3     26 |   DTTM_ALIAS,
235.3     27 |   ensureIsArray,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   AxisType,
235.3        |   ^^^^^^^^^
235.3   > 23 |   ChartDataResponseResult,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 24 |   DataRecord,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 25 |   DataRecordValue,
235.3        | ^^^^^^^^^^^^^^^^^^
235.3     26 |   DTTM_ALIAS,
235.3     27 |   ensureIsArray,
235.3     28 |   GenericDataType,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   AxisType,
235.3        |   ^^^^^^^^^
235.3   > 23 |   ChartDataResponseResult,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 24 |   DataRecord,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 25 |   DataRecordValue,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 26 |   DTTM_ALIAS,
235.3        | ^^^^^^^^^^^^^
235.3     27 |   ensureIsArray,
235.3     28 |   GenericDataType,
235.3     29 |   LegendState,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   AxisType,
235.3        |   ^^^^^^^^^
235.3   > 23 |   ChartDataResponseResult,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 24 |   DataRecord,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 25 |   DataRecordValue,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 26 |   DTTM_ALIAS,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 27 |   ensureIsArray,
235.3        | ^^^^^^^^^^^^^^^^
235.3     28 |   GenericDataType,
235.3     29 |   LegendState,
235.3     30 |   normalizeTimestamp,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   AxisType,
235.3        |   ^^^^^^^^^
235.3   > 23 |   ChartDataResponseResult,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 24 |   DataRecord,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 25 |   DataRecordValue,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 26 |   DTTM_ALIAS,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 27 |   ensureIsArray,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 28 |   GenericDataType,
235.3        | ^^^^^^^^^^^^^^^^^^
235.3     29 |   LegendState,
235.3     30 |   normalizeTimestamp,
235.3     31 |   NumberFormats,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   AxisType,
235.3        |   ^^^^^^^^^
235.3   > 23 |   ChartDataResponseResult,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 24 |   DataRecord,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 25 |   DataRecordValue,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 26 |   DTTM_ALIAS,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 27 |   ensureIsArray,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 28 |   GenericDataType,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 29 |   LegendState,
235.3        | ^^^^^^^^^^^^^^
235.3     30 |   normalizeTimestamp,
235.3     31 |   NumberFormats,
235.3     32 |   NumberFormatter,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   AxisType,
235.3        |   ^^^^^^^^^
235.3   > 23 |   ChartDataResponseResult,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 24 |   DataRecord,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 25 |   DataRecordValue,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 26 |   DTTM_ALIAS,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 27 |   ensureIsArray,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 28 |   GenericDataType,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 29 |   LegendState,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 30 |   normalizeTimestamp,
235.3        | ^^^^^^^^^^^^^^^^^^^^^
235.3     31 |   NumberFormats,
235.3     32 |   NumberFormatter,
235.3     33 |   SupersetTheme,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   AxisType,
235.3        |   ^^^^^^^^^
235.3   > 23 |   ChartDataResponseResult,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 24 |   DataRecord,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 25 |   DataRecordValue,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 26 |   DTTM_ALIAS,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 27 |   ensureIsArray,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 28 |   GenericDataType,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 29 |   LegendState,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 30 |   normalizeTimestamp,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 31 |   NumberFormats,
235.3        | ^^^^^^^^^^^^^^^^
235.3     32 |   NumberFormatter,
235.3     33 |   SupersetTheme,
235.3     34 |   TimeFormatter,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   AxisType,
235.3        |   ^^^^^^^^^
235.3   > 23 |   ChartDataResponseResult,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 24 |   DataRecord,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 25 |   DataRecordValue,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 26 |   DTTM_ALIAS,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 27 |   ensureIsArray,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 28 |   GenericDataType,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 29 |   LegendState,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 30 |   normalizeTimestamp,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 31 |   NumberFormats,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 32 |   NumberFormatter,
235.3        | ^^^^^^^^^^^^^^^^^^
235.3     33 |   SupersetTheme,
235.3     34 |   TimeFormatter,
235.3     35 |   ValueFormatter,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   AxisType,
235.3        |   ^^^^^^^^^
235.3   > 23 |   ChartDataResponseResult,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 24 |   DataRecord,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 25 |   DataRecordValue,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 26 |   DTTM_ALIAS,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 27 |   ensureIsArray,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 28 |   GenericDataType,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 29 |   LegendState,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 30 |   normalizeTimestamp,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 31 |   NumberFormats,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 32 |   NumberFormatter,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 33 |   SupersetTheme,
235.3        | ^^^^^^^^^^^^^^^^
235.3     34 |   TimeFormatter,
235.3     35 |   ValueFormatter,
235.3     36 | } from '@superset-ui/core';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   AxisType,
235.3        |   ^^^^^^^^^
235.3   > 23 |   ChartDataResponseResult,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 24 |   DataRecord,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 25 |   DataRecordValue,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 26 |   DTTM_ALIAS,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 27 |   ensureIsArray,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 28 |   GenericDataType,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 29 |   LegendState,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 30 |   normalizeTimestamp,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 31 |   NumberFormats,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 32 |   NumberFormatter,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 33 |   SupersetTheme,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 34 |   TimeFormatter,
235.3        | ^^^^^^^^^^^^^^^^
235.3     35 |   ValueFormatter,
235.3     36 | } from '@superset-ui/core';
235.3     37 | import { SortSeriesType, LegendPaddingType } from '@superset-ui/chart-controls';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:22:3
235.3 TS2695: Left side of comma operator is unused and has no side effects.
235.3     20 | import {
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3   > 22 |   AxisType,
235.3        |   ^^^^^^^^^
235.3   > 23 |   ChartDataResponseResult,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 24 |   DataRecord,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 25 |   DataRecordValue,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 26 |   DTTM_ALIAS,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 27 |   ensureIsArray,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 28 |   GenericDataType,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 29 |   LegendState,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 30 |   normalizeTimestamp,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 31 |   NumberFormats,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 32 |   NumberFormatter,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 33 |   SupersetTheme,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 34 |   TimeFormatter,
235.3        | ^^^^^^^^^^^^^^^^^^^^^^^^^^
235.3   > 35 |   ValueFormatter,
235.3        | ^^^^^^^^^^^^^^^^^
235.3     36 | } from '@superset-ui/core';
235.3     37 | import { SortSeriesType, LegendPaddingType } from '@superset-ui/chart-controls';
235.3     38 | import { format } from 'echarts/core';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:23:3
235.3 TS2304: Cannot find name 'ChartDataResponseResult'.
235.3     21 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
235.3     22 |   AxisType,
235.3   > 23 |   ChartDataResponseResult,
235.3        |   ^^^^^^^^^^^^^^^^^^^^^^^
235.3     24 |   DataRecord,
235.3     25 |   DataRecordValue,
235.3     26 |   DTTM_ALIAS,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:24:3
235.3 TS2304: Cannot find name 'DataRecord'.
235.3     22 |   AxisType,
235.3     23 |   ChartDataResponseResult,
235.3   > 24 |   DataRecord,
235.3        |   ^^^^^^^^^^
235.3     25 |   DataRecordValue,
235.3     26 |   DTTM_ALIAS,
235.3     27 |   ensureIsArray,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:25:3
235.3 TS2304: Cannot find name 'DataRecordValue'.
235.3     23 |   ChartDataResponseResult,
235.3     24 |   DataRecord,
235.3   > 25 |   DataRecordValue,
235.3        |   ^^^^^^^^^^^^^^^
235.3     26 |   DTTM_ALIAS,
235.3     27 |   ensureIsArray,
235.3     28 |   GenericDataType,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:26:3
235.3 TS2304: Cannot find name 'DTTM_ALIAS'.
235.3     24 |   DataRecord,
235.3     25 |   DataRecordValue,
235.3   > 26 |   DTTM_ALIAS,
235.3        |   ^^^^^^^^^^
235.3     27 |   ensureIsArray,
235.3     28 |   GenericDataType,
235.3     29 |   LegendState,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:27:3
235.3 TS2304: Cannot find name 'ensureIsArray'.
235.3     25 |   DataRecordValue,
235.3     26 |   DTTM_ALIAS,
235.3   > 27 |   ensureIsArray,
235.3        |   ^^^^^^^^^^^^^
235.3     28 |   GenericDataType,
235.3     29 |   LegendState,
235.3     30 |   normalizeTimestamp,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:28:3
235.3 TS2304: Cannot find name 'GenericDataType'.
235.3     26 |   DTTM_ALIAS,
235.3     27 |   ensureIsArray,
235.3   > 28 |   GenericDataType,
235.3        |   ^^^^^^^^^^^^^^^
235.3     29 |   LegendState,
235.3     30 |   normalizeTimestamp,
235.3     31 |   NumberFormats,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:29:3
235.3 TS2304: Cannot find name 'LegendState'.
235.3     27 |   ensureIsArray,
235.3     28 |   GenericDataType,
235.3   > 29 |   LegendState,
235.3        |   ^^^^^^^^^^^
235.3     30 |   normalizeTimestamp,
235.3     31 |   NumberFormats,
235.3     32 |   NumberFormatter,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:30:3
235.3 TS2304: Cannot find name 'normalizeTimestamp'.
235.3     28 |   GenericDataType,
235.3     29 |   LegendState,
235.3   > 30 |   normalizeTimestamp,
235.3        |   ^^^^^^^^^^^^^^^^^^
235.3     31 |   NumberFormats,
235.3     32 |   NumberFormatter,
235.3     33 |   SupersetTheme,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:31:3
235.3 TS2304: Cannot find name 'NumberFormats'.
235.3     29 |   LegendState,
235.3     30 |   normalizeTimestamp,
235.3   > 31 |   NumberFormats,
235.3        |   ^^^^^^^^^^^^^
235.3     32 |   NumberFormatter,
235.3     33 |   SupersetTheme,
235.3     34 |   TimeFormatter,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:32:3
235.3 TS2304: Cannot find name 'NumberFormatter'.
235.3     30 |   normalizeTimestamp,
235.3     31 |   NumberFormats,
235.3   > 32 |   NumberFormatter,
235.3        |   ^^^^^^^^^^^^^^^
235.3     33 |   SupersetTheme,
235.3     34 |   TimeFormatter,
235.3     35 |   ValueFormatter,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:33:3
235.3 TS2304: Cannot find name 'SupersetTheme'.
235.3     31 |   NumberFormats,
235.3     32 |   NumberFormatter,
235.3   > 33 |   SupersetTheme,
235.3        |   ^^^^^^^^^^^^^
235.3     34 |   TimeFormatter,
235.3     35 |   ValueFormatter,
235.3     36 | } from '@superset-ui/core';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:34:3
235.3 TS2304: Cannot find name 'TimeFormatter'.
235.3     32 |   NumberFormatter,
235.3     33 |   SupersetTheme,
235.3   > 34 |   TimeFormatter,
235.3        |   ^^^^^^^^^^^^^
235.3     35 |   ValueFormatter,
235.3     36 | } from '@superset-ui/core';
235.3     37 | import { SortSeriesType, LegendPaddingType } from '@superset-ui/chart-controls';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:35:3
235.3 TS2304: Cannot find name 'ValueFormatter'.
235.3     33 |   SupersetTheme,
235.3     34 |   TimeFormatter,
235.3   > 35 |   ValueFormatter,
235.3        |   ^^^^^^^^^^^^^^
235.3     36 | } from '@superset-ui/core';
235.3     37 | import { SortSeriesType, LegendPaddingType } from '@superset-ui/chart-controls';
235.3     38 | import { format } from 'echarts/core';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:36:3
235.3 TS2304: Cannot find name 'from'.
235.3     34 |   TimeFormatter,
235.3     35 |   ValueFormatter,
235.3   > 36 | } from '@superset-ui/core';
235.3        |   ^^^^
235.3     37 | import { SortSeriesType, LegendPaddingType } from '@superset-ui/chart-controls';
235.3     38 | import { format } from 'echarts/core';
235.3     39 | import type { LegendComponentOption } from 'echarts/components';
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:60:9
235.3 TS2304: Cannot find name 'DataRecord'.
235.3     58 |
235.3     59 | export function extractDataTotalValues(
235.3   > 60 |   data: DataRecord[],
235.3        |         ^^^^^^^^^^
235.3     61 |   opts: {
235.3     62 |     stack: StackType;
235.3     63 |     percentageThreshold: number;
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:65:19
235.3 TS2304: Cannot find name 'LegendState'.
235.3     63 |     percentageThreshold: number;
235.3     64 |     xAxisCol: string;
235.3   > 65 |     legendState?: LegendState;
235.3        |                   ^^^^^^^^^^^
235.3     66 |   },
235.3     67 | ): {
235.3     68 |   totalStackedValues: number[];
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:102:19
235.3 TS2304: Cannot find name 'LegendState'.
235.3     100 |     onlyTotal?: boolean;
235.3     101 |     isHorizontal?: boolean;
235.3   > 102 |     legendState?: LegendState;
235.3         |                   ^^^^^^^^^^^
235.3     103 |   },
235.3     104 | ): number[] {
235.3     105 |   const showValueIndexes: number[] = [];
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:135:9
235.3 TS2304: Cannot find name 'DataRecord'.
235.3     133 |
235.3     134 | export function sortAndFilterSeries(
235.3   > 135 |   rows: DataRecord[],
235.3         |         ^^^^^^^^^^
235.3     136 |   xAxis: string,
235.3     137 |   extraMetricLabels: any[],
235.3     138 |   sortSeriesType?: SortSeriesType,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:181:9
235.3 TS2304: Cannot find name 'DataRecord'.
235.3     179 |
235.3     180 | export function sortRows(
235.3   > 181 |   rows: DataRecord[],
235.3         |         ^^^^^^^^^^
235.3     182 |   totalStackedValues: number[],
235.3     183 |   xAxis: string,
235.3     184 |   xAxisSortSeries: SortSeriesType,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:188:18
235.3 TS2304: Cannot find name 'DataRecordValue'.
235.3     186 | ) {
235.3     187 |   const sortedRows = rows.map((row, idx) => {
235.3   > 188 |     let sortKey: DataRecordValue = '';
235.3         |                  ^^^^^^^^^^^^^^^
235.3     189 |     let aggregate: number | undefined;
235.3     190 |     let entries = 0;
235.3     191 |     Object.entries(row).forEach(([key, value]) => {
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:263:9
235.3 TS2304: Cannot find name 'DataRecord'.
235.3     261 |
235.3     262 | export function extractSeries(
235.3   > 263 |   data: DataRecord[],
235.3         |         ^^^^^^^^^^
235.3     264 |   opts: {
235.3     265 |     fillNeighborValue?: number;
235.3     266 |     xAxis?: string;
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:280:13
235.3 TS2304: Cannot find name 'DTTM_ALIAS'.
235.3     278 |   const {
235.3     279 |     fillNeighborValue,
235.3   > 280 |     xAxis = DTTM_ALIAS,
235.3         |             ^^^^^^^^^^
235.3     281 |     extraMetricLabels = [],
235.3     282 |     removeNulls = false,
235.3     283 |     stack = false,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:292:15
235.3 TS2304: Cannot find name 'DataRecord'.
235.3     290 |   } = opts;
235.3     291 |   if (data.length === 0) return [[], [], undefined];
235.3   > 292 |   const rows: DataRecord[] = data.map(datum => ({
235.3         |               ^^^^^^^^^^
235.3     293 |     ...datum,
235.3     294 |     [xAxis]: datum[xAxis],
235.3     295 |   }));
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:337:20
235.3 TS2304: Cannot find name 'DataRecordValue'.
235.3     335 |           isNextToDefinedValue &&
235.3     336 |           fillNeighborValue !== undefined;
235.3   > 337 |         let value: DataRecordValue | undefined = currentValue;
235.3         |                    ^^^^^^^^^^^^^^^
235.3     338 |         if (isFillNeighborValue) {
235.3     339 |           value = fillNeighborValue;
235.3     340 |         } else if (
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:359:9
235.3 TS2304: Cannot find name 'DataRecordValue'.
235.3     357 |
235.3     358 | export function formatSeriesName(
235.3   > 359 |   name: DataRecordValue | undefined,
235.3         |         ^^^^^^^^^^^^^^^
235.3     360 |   {
235.3     361 |     numberFormatter,
235.3     362 |     timeFormatter,
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:365:23
235.3 TS2304: Cannot find name 'ValueFormatter'.
235.3     363 |     coltype,
235.3     364 |   }: {
235.3   > 365 |     numberFormatter?: ValueFormatter;
235.3         |                       ^^^^^^^^^^^^^^
235.3     366 |     timeFormatter?: TimeFormatter;
235.3     367 |     coltype?: GenericDataType;
235.3     368 |   } = {},
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:366:21
235.3 TS2304: Cannot find name 'TimeFormatter'.
235.3     364 |   }: {
235.3     365 |     numberFormatter?: ValueFormatter;
235.3   > 366 |     timeFormatter?: TimeFormatter;
235.3         |                     ^^^^^^^^^^^^^
235.3     367 |     coltype?: GenericDataType;
235.3     368 |   } = {},
235.3     369 | ): string {
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:367:15
235.3 TS2304: Cannot find name 'GenericDataType'.
235.3     365 |     numberFormatter?: ValueFormatter;
235.3     366 |     timeFormatter?: TimeFormatter;
235.3   > 367 |     coltype?: GenericDataType;
235.3         |               ^^^^^^^^^^^^^^^
235.3     368 |   } = {},
235.3     369 | ): string {
235.3     370 |   if (name === undefined || name === null) {
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:376:43
235.3 TS2304: Cannot find name 'GenericDataType'.
235.3     374 |     return name.toString();
235.3     375 |   }
235.3   > 376 |   if (name instanceof Date || coltype === GenericDataType.Temporal) {
235.3         |                                           ^^^^^^^^^^^^^^^
235.3     377 |     const normalizedName =
235.3     378 |       typeof name === 'string' ? normalizeTimestamp(name) : name;
235.3     379 |     const d =
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:378:34
235.3 TS2304: Cannot find name 'normalizeTimestamp'.
235.3     376 |   if (name instanceof Date || coltype === GenericDataType.Temporal) {
235.3     377 |     const normalizedName =
235.3   > 378 |       typeof name === 'string' ? normalizeTimestamp(name) : name;
235.3         |                                  ^^^^^^^^^^^^^^^^^^
235.3     379 |     const d =
235.3     380 |       normalizedName instanceof Date
235.3     381 |         ? normalizedName
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:395:9
235.3 TS2304: Cannot find name 'ChartDataResponseResult'.
235.3     393 |   coltypes = [],
235.3     394 |   colnames = [],
235.3   > 395 | }: Pick<ChartDataResponseResult, 'coltypes' | 'colnames'>): Record<
235.3         |         ^^^^^^^^^^^^^^^^^^^^^^^
235.3     396 |   string,
235.3     397 |   GenericDataType
235.3     398 | > =>
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:397:3
235.3 TS2304: Cannot find name 'GenericDataType'.
235.3     395 | }: Pick<ChartDataResponseResult, 'coltypes' | 'colnames'>): Record<
235.3     396 |   string,
235.3   > 397 |   GenericDataType
235.3         |   ^^^^^^^^^^^^^^^
235.3     398 | > =>
235.3     399 |   colnames.reduce(
235.3     400 |     (accumulator, item, index) => ({ ...accumulator, [item]: coltypes[index] }),
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:411:11
235.3 TS2304: Cannot find name 'DataRecord'.
235.3     409 |   coltypeMapping = {},
235.3     410 | }: {
235.3   > 411 |   datum?: DataRecord;
235.3         |           ^^^^^^^^^^
235.3     412 |   groupby?: string[] | null;
235.3     413 |   numberFormatter?: NumberFormatter;
235.3     414 |   timeFormatter?: TimeFormatter;
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:413:21
235.3 TS2304: Cannot find name 'NumberFormatter'.
235.3     411 |   datum?: DataRecord;
235.3     412 |   groupby?: string[] | null;
235.3   > 413 |   numberFormatter?: NumberFormatter;
235.3         |                     ^^^^^^^^^^^^^^^
235.3     414 |   timeFormatter?: TimeFormatter;
235.3     415 |   coltypeMapping?: Record<string, GenericDataType>;
235.3     416 | }): string {
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:414:19
235.3 TS2304: Cannot find name 'TimeFormatter'.
235.3     412 |   groupby?: string[] | null;
235.3     413 |   numberFormatter?: NumberFormatter;
235.3   > 414 |   timeFormatter?: TimeFormatter;
235.3         |                   ^^^^^^^^^^^^^
235.3     415 |   coltypeMapping?: Record<string, GenericDataType>;
235.3     416 | }): string {
235.3     417 |   return ensureIsArray(groupby)
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:415:35
235.3 TS2304: Cannot find name 'GenericDataType'.
235.3     413 |   numberFormatter?: NumberFormatter;
235.3     414 |   timeFormatter?: TimeFormatter;
235.3   > 415 |   coltypeMapping?: Record<string, GenericDataType>;
235.3         |                                   ^^^^^^^^^^^^^^^
235.3     416 | }): string {
235.3     417 |   return ensureIsArray(groupby)
235.3     418 |     .map(val =>
235.3
235.3 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:417:10
235.3 TS2304: Cannot find name 'ensureIsArray'.
235.3     415 |   coltypeMapping?:
output clipped, log limit 2MiB reached]
241.4 90m 25 |   DataRecordValue,
241.4   > 26 |   DTTM_ALIAS,
241.4        |   ^^^^^^^^^^
241.4     27 |   ensureIsArray,
241.4     28 |   GenericDataType,
241.4     29 |   LegendState,
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:27:3
241.4 TS2304: Cannot find name 'ensureIsArray'.
241.4     25 |   DataRecordValue,
241.4     26 |   DTTM_ALIAS,
241.4   > 27 |   ensureIsArray,
241.4        |   ^^^^^^^^^^^^^
241.4     28 |   GenericDataType,
241.4     29 |   LegendState,
241.4     30 |   normalizeTimestamp,
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:28:3
241.4 TS2304: Cannot find name 'GenericDataType'.
241.4     26 |   DTTM_ALIAS,
241.4     27 |   ensureIsArray,
241.4   > 28 |   GenericDataType,
241.4        |   ^^^^^^^^^^^^^^^
241.4     29 |   LegendState,
241.4     30 |   normalizeTimestamp,
241.4     31 |   NumberFormats,
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:29:3
241.4 TS2304: Cannot find name 'LegendState'.
241.4     27 |   ensureIsArray,
241.4     28 |   GenericDataType,
241.4   > 29 |   LegendState,
241.4        |   ^^^^^^^^^^^
241.4     30 |   normalizeTimestamp,
241.4     31 |   NumberFormats,
241.4     32 |   NumberFormatter,
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:30:3
241.4 TS2304: Cannot find name 'normalizeTimestamp'.
241.4     28 |   GenericDataType,
241.4     29 |   LegendState,
241.4   > 30 |   normalizeTimestamp,
241.4        |   ^^^^^^^^^^^^^^^^^^
241.4     31 |   NumberFormats,
241.4     32 |   NumberFormatter,
241.4     33 |   SupersetTheme,
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:31:3
241.4 TS2304: Cannot find name 'NumberFormats'.
241.4     29 |   LegendState,
241.4     30 |   normalizeTimestamp,
241.4   > 31 |   NumberFormats,
241.4        |   ^^^^^^^^^^^^^
241.4     32 |   NumberFormatter,
241.4     33 |   SupersetTheme,
241.4     34 |   TimeFormatter,
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:32:3
241.4 TS2304: Cannot find name 'NumberFormatter'.
241.4     30 |   normalizeTimestamp,
241.4     31 |   NumberFormats,
241.4   > 32 |   NumberFormatter,
241.4        |   ^^^^^^^^^^^^^^^
241.4     33 |   SupersetTheme,
241.4     34 |   TimeFormatter,
241.4     35 |   ValueFormatter,
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:33:3
241.4 TS2304: Cannot find name 'SupersetTheme'.
241.4     31 |   NumberFormats,
241.4     32 |   NumberFormatter,
241.4   > 33 |   SupersetTheme,
241.4        |   ^^^^^^^^^^^^^
241.4     34 |   TimeFormatter,
241.4     35 |   ValueFormatter,
241.4     36 | } from '@superset-ui/core';
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:34:3
241.4 TS2304: Cannot find name 'TimeFormatter'.
241.4     32 |   NumberFormatter,
241.4     33 |   SupersetTheme,
241.4   > 34 |   TimeFormatter,
241.4        |   ^^^^^^^^^^^^^
241.4     35 |   ValueFormatter,
241.4     36 | } from '@superset-ui/core';
241.4     37 | import { SortSeriesType, LegendPaddingType } from '@superset-ui/chart-controls';
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:35:3
241.4 TS2304: Cannot find name 'ValueFormatter'.
241.4     33 |   SupersetTheme,
241.4     34 |   TimeFormatter,
241.4   > 35 |   ValueFormatter,
241.4        |   ^^^^^^^^^^^^^^
241.4     36 | } from '@superset-ui/core';
241.4     37 | import { SortSeriesType, LegendPaddingType } from '@superset-ui/chart-controls';
241.4     38 | import { format } from 'echarts/core';
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:36:3
241.4 TS2304: Cannot find name 'from'.
241.4     34 |   TimeFormatter,
241.4     35 |   ValueFormatter,
241.4   > 36 | } from '@superset-ui/core';
241.4        |   ^^^^
241.4     37 | import { SortSeriesType, LegendPaddingType } from '@superset-ui/chart-controls';
241.4     38 | import { format } from 'echarts/core';
241.4     39 | import type { LegendComponentOption } from 'echarts/components';
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:60:9
241.4 TS2304: Cannot find name 'DataRecord'.
241.4     58 |
241.4     59 | export function extractDataTotalValues(
241.4   > 60 |   data: DataRecord[],
241.4        |         ^^^^^^^^^^
241.4     61 |   opts: {
241.4     62 |     stack: StackType;
241.4     63 |     percentageThreshold: number;
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:65:19
241.4 TS2304: Cannot find name 'LegendState'.
241.4     63 |     percentageThreshold: number;
241.4     64 |     xAxisCol: string;
241.4   > 65 |     legendState?: LegendState;
241.4        |                   ^^^^^^^^^^^
241.4     66 |   },
241.4     67 | ): {
241.4     68 |   totalStackedValues: number[];
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:102:19
241.4 TS2304: Cannot find name 'LegendState'.
241.4     100 |     onlyTotal?: boolean;
241.4     101 |     isHorizontal?: boolean;
241.4   > 102 |     legendState?: LegendState;
241.4         |                   ^^^^^^^^^^^
241.4     103 |   },
241.4     104 | ): number[] {
241.4     105 |   const showValueIndexes: number[] = [];
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:135:9
241.4 TS2304: Cannot find name 'DataRecord'.
241.4     133 |
241.4     134 | export function sortAndFilterSeries(
241.4   > 135 |   rows: DataRecord[],
241.4         |         ^^^^^^^^^^
241.4     136 |   xAxis: string,
241.4     137 |   extraMetricLabels: any[],
241.4     138 |   sortSeriesType?: SortSeriesType,
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:181:9
241.4 TS2304: Cannot find name 'DataRecord'.
241.4     179 |
241.4     180 | export function sortRows(
241.4   > 181 |   rows: DataRecord[],
241.4         |         ^^^^^^^^^^
241.4     182 |   totalStackedValues: number[],
241.4     183 |   xAxis: string,
241.4     184 |   xAxisSortSeries: SortSeriesType,
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:188:18
241.4 TS2304: Cannot find name 'DataRecordValue'.
241.4     186 | ) {
241.4     187 |   const sortedRows = rows.map((row, idx) => {
241.4   > 188 |     let sortKey: DataRecordValue = '';
241.4         |                  ^^^^^^^^^^^^^^^
241.4     189 |     let aggregate: number | undefined;
241.4     190 |     let entries = 0;
241.4     191 |     Object.entries(row).forEach(([key, value]) => {
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:263:9
241.4 TS2304: Cannot find name 'DataRecord'.
241.4     261 |
241.4     262 | export function extractSeries(
241.4   > 263 |   data: DataRecord[],
241.4         |         ^^^^^^^^^^
241.4     264 |   opts: {
241.4     265 |     fillNeighborValue?: number;
241.4     266 |     xAxis?: string;
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:280:13
241.4 TS2304: Cannot find name 'DTTM_ALIAS'.
241.4     278 |   const {
241.4     279 |     fillNeighborValue,
241.4   > 280 |     xAxis = DTTM_ALIAS,
241.4         |             ^^^^^^^^^^
241.4     281 |     extraMetricLabels = [],
241.4     282 |     removeNulls = false,
241.4     283 |     stack = false,
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:292:15
241.4 TS2304: Cannot find name 'DataRecord'.
241.4     290 |   } = opts;
241.4     291 |   if (data.length === 0) return [[], [], undefined];
241.4   > 292 |   const rows: DataRecord[] = data.map(datum => ({
241.4         |               ^^^^^^^^^^
241.4     293 |     ...datum,
241.4     294 |     [xAxis]: datum[xAxis],
241.4     295 |   }));
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:337:20
241.4 TS2304: Cannot find name 'DataRecordValue'.
241.4     335 |           isNextToDefinedValue &&
241.4     336 |           fillNeighborValue !== undefined;
241.4   > 337 |         let value: DataRecordValue | undefined = currentValue;
241.4         |                    ^^^^^^^^^^^^^^^
241.4     338 |         if (isFillNeighborValue) {
241.4     339 |           value = fillNeighborValue;
241.4     340 |         } else if (
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:359:9
241.4 TS2304: Cannot find name 'DataRecordValue'.
241.4     357 |
241.4     358 | export function formatSeriesName(
241.4   > 359 |   name: DataRecordValue | undefined,
241.4         |         ^^^^^^^^^^^^^^^
241.4     360 |   {
241.4     361 |     numberFormatter,
241.4     362 |     timeFormatter,
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:365:23
241.4 TS2304: Cannot find name 'ValueFormatter'.
241.4     363 |     coltype,
241.4     364 |   }: {
241.4   > 365 |     numberFormatter?: ValueFormatter;
241.4         |                       ^^^^^^^^^^^^^^
241.4     366 |     timeFormatter?: TimeFormatter;
241.4     367 |     coltype?: GenericDataType;
241.4     368 |   } = {},
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:366:21
241.4 TS2304: Cannot find name 'TimeFormatter'.
241.4     364 |   }: {
241.4     365 |     numberFormatter?: ValueFormatter;
241.4   > 366 |     timeFormatter?: TimeFormatter;
241.4         |                     ^^^^^^^^^^^^^
241.4     367 |     coltype?: GenericDataType;
241.4     368 |   } = {},
241.4     369 | ): string {
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:367:15
241.4 TS2304: Cannot find name 'GenericDataType'.
241.4     365 |     numberFormatter?: ValueFormatter;
241.4     366 |     timeFormatter?: TimeFormatter;
241.4   > 367 |     coltype?: GenericDataType;
241.4         |               ^^^^^^^^^^^^^^^
241.4     368 |   } = {},
241.4     369 | ): string {
241.4     370 |   if (name === undefined || name === null) {
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:376:43
241.4 TS2304: Cannot find name 'GenericDataType'.
241.4     374 |     return name.toString();
241.4     375 |   }
241.4   > 376 |   if (name instanceof Date || coltype === GenericDataType.Temporal) {
241.4         |                                           ^^^^^^^^^^^^^^^
241.4     377 |     const normalizedName =
241.4     378 |       typeof name === 'string' ? normalizeTimestamp(name) : name;
241.4     379 |     const d =
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:378:34
241.4 TS2304: Cannot find name 'normalizeTimestamp'.
241.4     376 |   if (name instanceof Date || coltype === GenericDataType.Temporal) {
241.4     377 |     const normalizedName =
241.4   > 378 |       typeof name === 'string' ? normalizeTimestamp(name) : name;
241.4         |                                  ^^^^^^^^^^^^^^^^^^
241.4     379 |     const d =
241.4     380 |       normalizedName instanceof Date
241.4     381 |         ? normalizedName
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:395:9
241.4 TS2304: Cannot find name 'ChartDataResponseResult'.
241.4     393 |   coltypes = [],
241.4     394 |   colnames = [],
241.4   > 395 | }: Pick<ChartDataResponseResult, 'coltypes' | 'colnames'>): Record<
241.4         |         ^^^^^^^^^^^^^^^^^^^^^^^
241.4     396 |   string,
241.4     397 |   GenericDataType
241.4     398 | > =>
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:397:3
241.4 TS2304: Cannot find name 'GenericDataType'.
241.4     395 | }: Pick<ChartDataResponseResult, 'coltypes' | 'colnames'>): Record<
241.4     396 |   string,
241.4   > 397 |   GenericDataType
241.4         |   ^^^^^^^^^^^^^^^
241.4     398 | > =>
241.4     399 |   colnames.reduce(
241.4     400 |     (accumulator, item, index) => ({ ...accumulator, [item]: coltypes[index] }),
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:411:11
241.4 TS2304: Cannot find name 'DataRecord'.
241.4     409 |   coltypeMapping = {},
241.4     410 | }: {
241.4   > 411 |   datum?: DataRecord;
241.4         |           ^^^^^^^^^^
241.4     412 |   groupby?: string[] | null;
241.4     413 |   numberFormatter?: NumberFormatter;
241.4     414 |   timeFormatter?: TimeFormatter;
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:413:21
241.4 TS2304: Cannot find name 'NumberFormatter'.
241.4     411 |   datum?: DataRecord;
241.4     412 |   groupby?: string[] | null;
241.4   > 413 |   numberFormatter?: NumberFormatter;
241.4         |                     ^^^^^^^^^^^^^^^
241.4     414 |   timeFormatter?: TimeFormatter;
241.4     415 |   coltypeMapping?: Record<string, GenericDataType>;
241.4     416 | }): string {
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:414:19
241.4 TS2304: Cannot find name 'TimeFormatter'.
241.4     412 |   groupby?: string[] | null;
241.4     413 |   numberFormatter?: NumberFormatter;
241.4   > 414 |   timeFormatter?: TimeFormatter;
241.4         |                   ^^^^^^^^^^^^^
241.4     415 |   coltypeMapping?: Record<string, GenericDataType>;
241.4     416 | }): string {
241.4     417 |   return ensureIsArray(groupby)
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:415:35
241.4 TS2304: Cannot find name 'GenericDataType'.
241.4     413 |   numberFormatter?: NumberFormatter;
241.4     414 |   timeFormatter?: TimeFormatter;
241.4   > 415 |   coltypeMapping?: Record<string, GenericDataType>;
241.4         |                                   ^^^^^^^^^^^^^^^
241.4     416 | }): string {
241.4     417 |   return ensureIsArray(groupby)
241.4     418 |     .map(val =>
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:417:10
241.4 TS2304: Cannot find name 'ensureIsArray'.
241.4     415 |   coltypeMapping?: Record<string, GenericDataType>;
241.4     416 | }): string {
241.4   > 417 |   return ensureIsArray(groupby)
241.4         |          ^^^^^^^^^^^^^
241.4     418 |     .map(val =>
241.4     419 |       formatSeriesName(datum[val], {
241.4     420 |         numberFormatter,
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:432:10
241.4 TS2304: Cannot find name 'SupersetTheme'.
241.4     430 |   orientation: LegendOrientation,
241.4     431 |   show: boolean,
241.4   > 432 |   theme: SupersetTheme,
241.4         |          ^^^^^^^^^^^^^
241.4     433 |   zoomable = false,
241.4     434 |   legendState?: LegendState,
241.4     435 |   padding?: LegendPaddingType,
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:434:17
241.4 TS2304: Cannot find name 'LegendState'.
241.4     432 |   theme: SupersetTheme,
241.4     433 |   zoomable = false,
241.4   > 434 |   legendState?: LegendState,
241.4         |                 ^^^^^^^^^^^
241.4     435 |   padding?: LegendPaddingType,
241.4     436 | ): LegendComponentOption | LegendComponentOption[] {
241.4     437 |   const legend: LegendComponentOption | LegendComponentOption[] = {
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:562:14
241.4 TS2304: Cannot find name 'GenericDataType'.
241.4     560 |   stack: StackType,
241.4     561 |   forceCategorical?: boolean,
241.4   > 562 |   dataType?: GenericDataType,
241.4         |              ^^^^^^^^^^^^^^^
241.4     563 | ): AxisType {
241.4     564 |   if (forceCategorical) {
241.4     565 |     return AxisType.Category;
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:563:4
241.4 TS2304: Cannot find name 'AxisType'.
241.4     561 |   forceCategorical?: boolean,
241.4     562 |   dataType?: GenericDataType,
241.4   > 563 | ): AxisType {
241.4         |    ^^^^^^^^
241.4     564 |   if (forceCategorical) {
241.4     565 |     return AxisType.Category;
241.4     566 |   }
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:565:12
241.4 TS2304: Cannot find name 'AxisType'.
241.4     563 | ): AxisType {
241.4     564 |   if (forceCategorical) {
241.4   > 565 |     return AxisType.Category;
241.4         |            ^^^^^^^^
241.4     566 |   }
241.4     567 |   if (dataType === GenericDataType.Temporal) {
241.4     568 |     return AxisType.Time;
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:567:20
241.4 TS2304: Cannot find name 'GenericDataType'.
241.4     565 |     return AxisType.Category;
241.4     566 |   }
241.4   > 567 |   if (dataType === GenericDataType.Temporal) {
241.4         |                    ^^^^^^^^^^^^^^^
241.4     568 |     return AxisType.Time;
241.4     569 |   }
241.4     570 |   if (dataType === GenericDataType.Numeric && !stack) {
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:568:12
241.4 TS2304: Cannot find name 'AxisType'.
241.4     566 |   }
241.4     567 |   if (dataType === GenericDataType.Temporal) {
241.4   > 568 |     return AxisType.Time;
241.4         |            ^^^^^^^^
241.4     569 |   }
241.4     570 |   if (dataType === GenericDataType.Numeric && !stack) {
241.4     571 |     return AxisType.Value;
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:570:20
241.4 TS2304: Cannot find name 'GenericDataType'.
241.4     568 |     return AxisType.Time;
241.4     569 |   }
241.4   > 570 |   if (dataType === GenericDataType.Numeric && !stack) {
241.4         |                    ^^^^^^^^^^^^^^^
241.4     571 |     return AxisType.Value;
241.4     572 |   }
241.4     573 |   return AxisType.Category;
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:571:12
241.4 TS2304: Cannot find name 'AxisType'.
241.4     569 |   }
241.4     570 |   if (dataType === GenericDataType.Numeric && !stack) {
241.4   > 571 |     return AxisType.Value;
241.4         |            ^^^^^^^^
241.4     572 |   }
241.4     573 |   return AxisType.Category;
241.4     574 | }
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:573:10
241.4 TS2304: Cannot find name 'AxisType'.
241.4     571 |     return AxisType.Value;
241.4     572 |   }
241.4   > 573 |   return AxisType.Category;
241.4         |          ^^^^^^^^
241.4     574 | }
241.4     575 |
241.4     576 | export function getOverMaxHiddenFormatter(
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:579:17
241.4 TS2304: Cannot find name 'ValueFormatter'.
241.4     577 |   config: {
241.4     578 |     max?: number;
241.4   > 579 |     formatter?: ValueFormatter;
241.4         |                 ^^^^^^^^^^^^^^
241.4     580 |   } = {},
241.4     581 | ) {
241.4     582 |   const { max, formatter } = config;
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:586:14
241.4 TS2304: Cannot find name 'NumberFormatter'.
241.4     584 |   const shouldHideIfOverMax = !!max || max === 0;
241.4     585 |
241.4   > 586 |   return new NumberFormatter({
241.4         |              ^^^^^^^^^^^^^^^
241.4     587 |     formatFunc: value =>
241.4     588 |       `${
241.4     589 |         shouldHideIfOverMax && value > max
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:593:9
241.4 TS2304: Cannot find name 'NumberFormats'.
241.4     591 |           : formatter?.format(value) || value
241.4     592 |       }`,
241.4   > 593 |     id: NumberFormats.OVER_MAX_HIDDEN,
241.4         |         ^^^^^^^^^^^^^
241.4     594 |   });
241.4     595 | }
241.4     596 |
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:609:13
241.4 TS2304: Cannot find name 'AxisType'.
241.4     607 |
241.4     608 | export function getMinAndMaxFromBounds(
241.4   > 609 |   axisType: AxisType,
241.4         |             ^^^^^^^^
241.4     610 |   truncateAxis: boolean,
241.4     611 |   min?: number,
241.4     612 |   max?: number,
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/utils/series.ts:615:20
241.4 TS2304: Cannot find name 'AxisType'.
241.4     613 |   seriesType?: EchartsTimeseriesSeriesType,
241.4     614 | ): BoundsType | {} {
241.4   > 615 |   if (axisType === AxisType.Value && truncateAxis) {
241.4         |                    ^^^^^^^^
241.4     616 |     const ret: BoundsType = {};
241.4     617 |     if (seriesType === EchartsTimeseriesSeriesType.Bar) {
241.4     618 |       ret.scale = true;
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/buildQuery.ts:20:8
241.4 TS1141: String literal expected.
241.4     18 |  */
241.4     19 | import {
241.4   > 20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
241.4        |        ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
241.4     21 |   buildQueryContext,
241.4     22 |   ensureIsArray,
241.4     23 |   QueryFormData,
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/buildQuery.ts:20:118
241.4 TS2304: Cannot find name 'from'.
241.4     18 |  */
241.4     19 | import {
241.4   > 20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
241.4        |                                                                                                                      ^^^^
241.4     21 |   buildQueryContext,
241.4     22 |   ensureIsArray,
241.4     23 |   QueryFormData,
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/buildQuery.ts:21:3
241.4 TS2304: Cannot find name 'buildQueryContext'.
241.4     19 | import {
241.4     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
241.4   > 21 |   buildQueryContext,
241.4        |   ^^^^^^^^^^^^^^^^^
241.4     22 |   ensureIsArray,
241.4     23 |   QueryFormData,
241.4     24 | } from '@superset-ui/core';
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/buildQuery.ts:21:3
241.4 TS2695: Left side of comma operator is unused and has no side effects.
241.4     19 | import {
241.4     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
241.4   > 21 |   buildQueryContext,
241.4        |   ^^^^^^^^^^^^^^^^^
241.4     22 |   ensureIsArray,
241.4     23 |   QueryFormData,
241.4     24 | } from '@superset-ui/core';
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/buildQuery.ts:21:3
241.4 TS2695: Left side of comma operator is unused and has no side effects.
241.4     19 | import {
241.4     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
241.4   > 21 |   buildQueryContext,
241.4        |   ^^^^^^^^^^^^^^^^^^
241.4   > 22 |   ensureIsArray,
241.4        | ^^^^^^^^^^^^^^^^
241.4     23 |   QueryFormData,
241.4     24 | } from '@superset-ui/core';
241.4     25 |
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/buildQuery.ts:21:3
241.4 TS2695: Left side of comma operator is unused and has no side effects.
241.4     19 | import {
241.4     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
241.4   > 21 |   buildQueryContext,
241.4        |   ^^^^^^^^^^^^^^^^^^
241.4   > 22 |   ensureIsArray,
241.4        | ^^^^^^^^^^^^^^^^
241.4   > 23 |   QueryFormData,
241.4        | ^^^^^^^^^^^^^^^^
241.4     24 | } from '@superset-ui/core';
241.4     25 |
241.4     26 | export default function buildQuery(formData: QueryFormData) {
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/buildQuery.ts:22:3
241.4 TS2304: Cannot find name 'ensureIsArray'.
241.4     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
241.4     21 |   buildQueryContext,
241.4   > 22 |   ensureIsArray,
241.4        |   ^^^^^^^^^^^^^
241.4     23 |   QueryFormData,
241.4     24 | } from '@superset-ui/core';
241.4     25 |
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/buildQuery.ts:23:3
241.4 TS2304: Cannot find name 'QueryFormData'.
241.4     21 |   buildQueryContext,
241.4     22 |   ensureIsArray,
241.4   > 23 |   QueryFormData,
241.4        |   ^^^^^^^^^^^^^
241.4     24 | } from '@superset-ui/core';
241.4     25 |
241.4     26 | export default function buildQuery(formData: QueryFormData) {
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/buildQuery.ts:24:3
241.4 TS2304: Cannot find name 'from'.
241.4     22 |   ensureIsArray,
241.4     23 |   QueryFormData,
241.4   > 24 | } from '@superset-ui/core';
241.4        |   ^^^^
241.4     25 |
241.4     26 | export default function buildQuery(formData: QueryFormData) {
241.4     27 |   const { x_axis, granularity_sqla, groupby } = formData;
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/buildQuery.ts:26:46
241.4 TS2304: Cannot find name 'QueryFormData'.
241.4     24 | } from '@superset-ui/core';
241.4     25 |
241.4   > 26 | export default function buildQuery(formData: QueryFormData) {
241.4        |                                              ^^^^^^^^^^^^^
241.4     27 |   const { x_axis, granularity_sqla, groupby } = formData;
241.4     28 |   const columns = [
241.4     29 |     ...ensureIsArray(x_axis || granularity_sqla),
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/buildQuery.ts:29:8
241.4 TS2304: Cannot find name 'ensureIsArray'.
241.4     27 |   const { x_axis, granularity_sqla, groupby } = formData;
241.4     28 |   const columns = [
241.4   > 29 |     ...ensureIsArray(x_axis || granularity_sqla),
241.4        |        ^^^^^^^^^^^^^
241.4     30 |     ...ensureIsArray(groupby),
241.4     31 |   ];
241.4     32 |   return buildQueryContext(formData, baseQueryObject => [
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/buildQuery.ts:30:8
241.4 TS2304: Cannot find name 'ensureIsArray'.
241.4     28 |   const columns = [
241.4     29 |     ...ensureIsArray(x_axis || granularity_sqla),
241.4   > 30 |     ...ensureIsArray(groupby),
241.4        |        ^^^^^^^^^^^^^
241.4     31 |   ];
241.4     32 |   return buildQueryContext(formData, baseQueryObject => [
241.4     33 |     {
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/buildQuery.ts:32:10
241.4 TS2304: Cannot find name 'buildQueryContext'.
241.4     30 |     ...ensureIsArray(groupby),
241.4     31 |   ];
241.4   > 32 |   return buildQueryContext(formData, baseQueryObject => [
241.4        |          ^^^^^^^^^^^^^^^^^
241.4     33 |     {
241.4     34 |       ...baseQueryObject,
241.4     35 |       columns,
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/index.ts:33:3
241.4 TS2344: Type 'EchartsWaterfallChartProps' does not satisfy the constraint 'ChartProps<PlainObject>'.
241.4   Type 'EchartsWaterfallChartProps' is missing the following properties from type 'ChartProps<PlainObject>': annotationData, datasource, rawDatasource, initialValues, and 8 more.
241.4     31 | export default class EchartsWaterfallChartPlugin extends ChartPlugin<
241.4     32 |   EchartsWaterfallFormData,
241.4   > 33 |   EchartsWaterfallChartProps
241.4        |   ^^^^^^^^^^^^^^^^^^^^^^^^^^
241.4     34 | > {
241.4     35 |   /**
241.4     36 |    * The constructor is used to pass relevant metadata and callbacks that get
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/transformProps.ts:20:8
241.4 TS1141: String literal expected.
241.4     18 |  */
241.4     19 | import {
241.4   > 20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
241.4        |        ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
241.4     21 |   CurrencyFormatter,
241.4     22 |   DataRecord,
241.4     23 |   ensureIsArray,
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/transformProps.ts:20:118
241.4 TS2304: Cannot find name 'from'.
241.4     18 |  */
241.4     19 | import {
241.4   > 20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
241.4        |                                                                                                                      ^^^^
241.4     21 |   CurrencyFormatter,
241.4     22 |   DataRecord,
241.4     23 |   ensureIsArray,
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/transformProps.ts:21:3
241.4 TS2304: Cannot find name 'CurrencyFormatter'.
241.4     19 | import {
241.4     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
241.4   > 21 |   CurrencyFormatter,
241.4        |   ^^^^^^^^^^^^^^^^^
241.4     22 |   DataRecord,
241.4     23 |   ensureIsArray,
241.4     24 |   GenericDataType,
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/transformProps.ts:21:3
241.4 TS2695: Left side of comma operator is unused and has no side effects.
241.4     19 | import {
241.4     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
241.4   > 21 |   CurrencyFormatter,
241.4        |   ^^^^^^^^^^^^^^^^^
241.4     22 |   DataRecord,
241.4     23 |   ensureIsArray,
241.4     24 |   GenericDataType,
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/transformProps.ts:21:3
241.4 TS2695: Left side of comma operator is unused and has no side effects.
241.4     19 | import {
241.4     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
241.4   > 21 |   CurrencyFormatter,
241.4        |   ^^^^^^^^^^^^^^^^^^
241.4   > 22 |   DataRecord,
241.4        | ^^^^^^^^^^^^^
241.4     23 |   ensureIsArray,
241.4     24 |   GenericDataType,
241.4     25 |   getMetricLabel,
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/transformProps.ts:21:3
241.4 TS2695: Left side of comma operator is unused and has no side effects.
241.4     19 | import {
241.4     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
241.4   > 21 |   CurrencyFormatter,
241.4        |   ^^^^^^^^^^^^^^^^^^
241.4   > 22 |   DataRecord,
241.4        | ^^^^^^^^^^^^^
241.4   > 23 |   ensureIsArray,
241.4        | ^^^^^^^^^^^^^^^^
241.4     24 |   GenericDataType,
241.4     25 |   getMetricLabel,
241.4     26 |   getNumberFormatter,
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/transformProps.ts:21:3
241.4 TS2695: Left side of comma operator is unused and has no side effects.
241.4     19 | import {
241.4     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
241.4   > 21 |   CurrencyFormatter,
241.4        |   ^^^^^^^^^^^^^^^^^^
241.4   > 22 |   DataRecord,
241.4        | ^^^^^^^^^^^^^
241.4   > 23 |   ensureIsArray,
241.4        | ^^^^^^^^^^^^^
241.4   > 24 |   GenericDataType,
241.4        | ^^^^^^^^^^^^^^^^^^
241.4     25 |   getMetricLabel,
241.4     26 |   getNumberFormatter,
241.4     27 |   getTimeFormatter,
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/transformProps.ts:21:3
241.4 TS2695: Left side of comma operator is unused and has no side effects.
241.4     19 | import {
241.4     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
241.4   > 21 |   CurrencyFormatter,
241.4        |   ^^^^^^^^^^^^^^^^^^
241.4   > 22 |   DataRecord,
241.4        | ^^^^^^^^^^^^^
241.4   > 23 |   ensureIsArray,
241.4        | ^^^^^^^^^^^^^
241.4   > 24 |   GenericDataType,
241.4        | ^^^^^^^^^^^^^
241.4   > 25 |   getMetricLabel,
241.4        | ^^^^^^^^^^^^^^^^^
241.4     26 |   getNumberFormatter,
241.4     27 |   getTimeFormatter,
241.4     28 |   isAdhocColumn,
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/transformProps.ts:21:3
241.4 TS2695: Left side of comma operator is unused and has no side effects.
241.4     19 | import {
241.4     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
241.4   > 21 |   CurrencyFormatter,
241.4        |   ^^^^^^^^^^^^^^^^^^
241.4   > 22 |   DataRecord,
241.4        | ^^^^^^^^^^^^^
241.4   > 23 |   ensureIsArray,
241.4        | ^^^^^^^^^^^^^
241.4   > 24 |   GenericDataType,
241.4        | ^^^^^^^^^^^^^
241.4   > 25 |   getMetricLabel,
241.4        | ^^^^^^^^^^^^^
241.4   > 26 |   getNumberFormatter,
241.4        | ^^^^^^^^^^^^^^^^^^^^^
241.4     27 |   getTimeFormatter,
241.4     28 |   isAdhocColumn,
241.4     29 |   NumberFormatter,
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/transformProps.ts:21:3
241.4 TS2695: Left side of comma operator is unused and has no side effects.
241.4     19 | import {
241.4     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
241.4   > 21 |   CurrencyFormatter,
241.4        |   ^^^^^^^^^^^^^^^^^^
241.4   > 22 |   DataRecord,
241.4        | ^^^^^^^^^^^^^
241.4   > 23 |   ensureIsArray,
241.4        | ^^^^^^^^^^^^^
241.4   > 24 |   GenericDataType,
241.4        | ^^^^^^^^^^^^^
241.4   > 25 |   getMetricLabel,
241.4        | ^^^^^^^^^^^^^
241.4   > 26 |   getNumberFormatter,
241.4        | ^^^^^^^^^^^^^
241.4   > 27 |   getTimeFormatter,
241.4        | ^^^^^^^^^^^^^^^^^^^
241.4     28 |   isAdhocColumn,
241.4     29 |   NumberFormatter,
241.4     30 |   rgbToHex,
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/transformProps.ts:21:3
241.4 TS2695: Left side of comma operator is unused and has no side effects.
241.4     19 | import {
241.4     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
241.4   > 21 |   CurrencyFormatter,
241.4        |   ^^^^^^^^^^^^^^^^^^
241.4   > 22 |   DataRecord,
241.4        | ^^^^^^^^^^^^^
241.4   > 23 |   ensureIsArray,
241.4        | ^^^^^^^^^^^^^
241.4   > 24 |   GenericDataType,
241.4        | ^^^^^^^^^^^^^
241.4   > 25 |   getMetricLabel,
241.4        | ^^^^^^^^^^^^^
241.4   > 26 |   getNumberFormatter,
241.4        | ^^^^^^^^^^^^^
241.4   > 27 |   getTimeFormatter,
241.4        | ^^^^^^^^^^^^^
241.4   > 28 |   isAdhocColumn,
241.4        | ^^^^^^^^^^^^^^^^
241.4     29 |   NumberFormatter,
241.4     30 |   rgbToHex,
241.4     31 |   tooltipHtml,
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/transformProps.ts:21:3
241.4 TS2695: Left side of comma operator is unused and has no side effects.
241.4     19 | import {
241.4     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
241.4   > 21 |   CurrencyFormatter,
241.4        |   ^^^^^^^^^^^^^^^^^^
241.4   > 22 |   DataRecord,
241.4        | ^^^^^^^^^^^^^
241.4   > 23 |   ensureIsArray,
241.4        | ^^^^^^^^^^^^^
241.4   > 24 |   GenericDataType,
241.4        | ^^^^^^^^^^^^^
241.4   > 25 |   getMetricLabel,
241.4        | ^^^^^^^^^^^^^
241.4   > 26 |   getNumberFormatter,
241.4        | ^^^^^^^^^^^^^
241.4   > 27 |   getTimeFormatter,
241.4        | ^^^^^^^^^^^^^
241.4   > 28 |   isAdhocColumn,
241.4        | ^^^^^^^^^^^^^
241.4   > 29 |   NumberFormatter,
241.4        | ^^^^^^^^^^^^^^^^^^
241.4     30 |   rgbToHex,
241.4     31 |   tooltipHtml,
241.4     32 | } from '@superset-ui/core';
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/transformProps.ts:21:3
241.4 TS2695: Left side of comma operator is unused and has no side effects.
241.4     19 | import {
241.4     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
241.4   > 21 |   CurrencyFormatter,
241.4        |   ^^^^^^^^^^^^^^^^^^
241.4   > 22 |   DataRecord,
241.4        | ^^^^^^^^^^^^^
241.4   > 23 |   ensureIsArray,
241.4        | ^^^^^^^^^^^^^
241.4   > 24 |   GenericDataType,
241.4        | ^^^^^^^^^^^^^
241.4   > 25 |   getMetricLabel,
241.4        | ^^^^^^^^^^^^^
241.4   > 26 |   getNumberFormatter,
241.4        | ^^^^^^^^^^^^^
241.4   > 27 |   getTimeFormatter,
241.4        | ^^^^^^^^^^^^^
241.4   > 28 |   isAdhocColumn,
241.4        | ^^^^^^^^^^^^^
241.4   > 29 |   NumberFormatter,
241.4        | ^^^^^^^^^^^^^
241.4   > 30 |   rgbToHex,
241.4        | ^^^^^^^^^^^
241.4     31 |   tooltipHtml,
241.4     32 | } from '@superset-ui/core';
241.4     33 | import type { ComposeOption } from 'echarts/core';
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/transformProps.ts:21:3
241.4 TS2695: Left side of comma operator is unused and has no side effects.
241.4     19 | import {
241.4     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
241.4   > 21 |   CurrencyFormatter,
241.4        |   ^^^^^^^^^^^^^^^^^^
241.4   > 22 |   DataRecord,
241.4        | ^^^^^^^^^^^^^
241.4   > 23 |   ensureIsArray,
241.4        | ^^^^^^^^^^^^^
241.4   > 24 |   GenericDataType,
241.4        | ^^^^^^^^^^^^^
241.4   > 25 |   getMetricLabel,
241.4        | ^^^^^^^^^^^^^
241.4   > 26 |   getNumberFormatter,
241.4        | ^^^^^^^^^^^^^
241.4   > 27 |   getTimeFormatter,
241.4        | ^^^^^^^^^^^^^
241.4   > 28 |   isAdhocColumn,
241.4        | ^^^^^^^^^^^^^
241.4   > 29 |   NumberFormatter,
241.4        | ^^^^^^^^^^^^^
241.4   > 30 |   rgbToHex,
241.4        | ^^^^^^^^^^^^^
241.4   > 31 |   tooltipHtml,
241.4        | ^^^^^^^^^^^^^^
241.4     32 | } from '@superset-ui/core';
241.4     33 | import type { ComposeOption } from 'echarts/core';
241.4     34 | import type { BarSeriesOption } from 'echarts/charts';
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/transformProps.ts:22:3
241.4 TS2304: Cannot find name 'DataRecord'.
241.4     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
241.4     21 |   CurrencyFormatter,
241.4   > 22 |   DataRecord,
241.4        |   ^^^^^^^^^^
241.4     23 |   ensureIsArray,
241.4     24 |   GenericDataType,
241.4     25 |   getMetricLabel,
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/transformProps.ts:23:3
241.4 TS2304: Cannot find name 'ensureIsArray'.
241.4     21 |   CurrencyFormatter,
241.4     22 |   DataRecord,
241.4   > 23 |   ensureIsArray,
241.4        |   ^^^^^^^^^^^^^
241.4     24 |   GenericDataType,
241.4     25 |   getMetricLabel,
241.4     26 |   getNumberFormatter,
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/transformProps.ts:24:3
241.4 TS2304: Cannot find name 'GenericDataType'.
241.4     22 |   DataRecord,
241.4     23 |   ensureIsArray,
241.4   > 24 |   GenericDataType,
241.4        |   ^^^^^^^^^^^^^^^
241.4     25 |   getMetricLabel,
241.4     26 |   getNumberFormatter,
241.4     27 |   getTimeFormatter,
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/transformProps.ts:25:3
241.4 TS2304: Cannot find name 'getMetricLabel'.
241.4     23 |   ensureIsArray,
241.4     24 |   GenericDataType,
241.4   > 25 |   getMetricLabel,
241.4        |   ^^^^^^^^^^^^^^
241.4     26 |   getNumberFormatter,
241.4     27 |   getTimeFormatter,
241.4     28 |   isAdhocColumn,
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/transformProps.ts:26:3
241.4 TS2304: Cannot find name 'getNumberFormatter'.
241.4     24 |   GenericDataType,
241.4     25 |   getMetricLabel,
241.4   > 26 |   getNumberFormatter,
241.4        |   ^^^^^^^^^^^^^^^^^^
241.4     27 |   getTimeFormatter,
241.4     28 |   isAdhocColumn,
241.4     29 |   NumberFormatter,
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/transformProps.ts:27:3
241.4 TS2304: Cannot find name 'getTimeFormatter'.
241.4     25 |   getMetricLabel,
241.4     26 |   getNumberFormatter,
241.4   > 27 |   getTimeFormatter,
241.4        |   ^^^^^^^^^^^^^^^^
241.4     28 |   isAdhocColumn,
241.4     29 |   NumberFormatter,
241.4     30 |   rgbToHex,
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/transformProps.ts:28:3
241.4 TS2304: Cannot find name 'isAdhocColumn'.
241.4     26 |   getNumberFormatter,
241.4     27 |   getTimeFormatter,
241.4   > 28 |   isAdhocColumn,
241.4        |   ^^^^^^^^^^^^^
241.4     29 |   NumberFormatter,
241.4     30 |   rgbToHex,
241.4     31 |   tooltipHtml,
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/transformProps.ts:29:3
241.4 TS2304: Cannot find name 'NumberFormatter'.
241.4     27 |   getTimeFormatter,
241.4     28 |   isAdhocColumn,
241.4   > 29 |   NumberFormatter,
241.4        |   ^^^^^^^^^^^^^^^
241.4     30 |   rgbToHex,
241.4     31 |   tooltipHtml,
241.4     32 | } from '@superset-ui/core';
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/transformProps.ts:30:3
241.4 TS2304: Cannot find name 'rgbToHex'.
241.4     28 |   isAdhocColumn,
241.4     29 |   NumberFormatter,
241.4   > 30 |   rgbToHex,
241.4        |   ^^^^^^^^
241.4     31 |   tooltipHtml,
241.4     32 | } from '@superset-ui/core';
241.4     33 | import type { ComposeOption } from 'echarts/core';
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/transformProps.ts:31:3
241.4 TS2304: Cannot find name 'tooltipHtml'.
241.4     29 |   NumberFormatter,
241.4     30 |   rgbToHex,
241.4   > 31 |   tooltipHtml,
241.4        |   ^^^^^^^^^^^
241.4     32 | } from '@superset-ui/core';
241.4     33 | import type { ComposeOption } from 'echarts/core';
241.4     34 | import type { BarSeriesOption } from 'echarts/charts';
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/transformProps.ts:32:3
241.4 TS2304: Cannot find name 'from'.
241.4     30 |   rgbToHex,
241.4     31 |   tooltipHtml,
241.4   > 32 | } from '@superset-ui/core';
241.4        |   ^^^^
241.4     33 | import type { ComposeOption } from 'echarts/core';
241.4     34 | import type { BarSeriesOption } from 'echarts/charts';
241.4     35 | import {
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/transformProps.ts:58:21
241.4 TS2304: Cannot find name 'NumberFormatter'.
241.4     56 |   params: ICallbackDataParams[];
241.4     57 |   breakdownName?: string;
241.4   > 58 |   defaultFormatter: NumberFormatter | CurrencyFormatter;
241.4        |                     ^^^^^^^^^^^^^^^
241.4     59 |   xAxisFormatter: (value: number | string, index: number) => string;
241.4     60 | }) {
241.4     61 |   const series = params.find(
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/transformProps.ts:58:39
241.4 TS2304: Cannot find name 'CurrencyFormatter'.
241.4     56 |   params: ICallbackDataParams[];
241.4     57 |   breakdownName?: string;
241.4   > 58 |   defaultFormatter: NumberFormatter | CurrencyFormatter;
241.4        |                                       ^^^^^^^^^^^^^^^^^
241.4     59 |   xAxisFormatter: (value: number | string, index: number) => string;
241.4     60 | }) {
241.4     61 |   const series = params.find(
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/transformProps.ts:87:10
241.4 TS2304: Cannot find name 'tooltipHtml'.
241.4     85 |   }
241.4     86 |   rows.push([TOTAL_MARK, defaultFormatter(series.data.totalSum)]);
241.4   > 87 |   return tooltipHtml(rows, title);
241.4        |          ^^^^^^^^^^^
241.4     88 | }
241.4     89 |
241.4     90 | function transformer({
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/transformProps.ts:96:9
241.4 TS2304: Cannot find name 'DataRecord'.
241.4     94 |   breakdown,
241.4     95 | }: {
241.4   > 96 |   data: DataRecord[];
241.4        |         ^^^^^^^^^^
241.4     97 |   xAxis: string;
241.4     98 |   metric: string;
241.4     99 |   breakdown?: string;
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/transformProps.ts:108:22
241.4 TS2304: Cannot find name 'DataRecord'.
241.4     106 |     acc.set(categoryLabel, categoryData);
241.4     107 |     return acc;
241.4   > 108 |   }, new Map<string, DataRecord[]>());
241.4         |                      ^^^^^^^^^^
241.4     109 |
241.4     110 |   const transformedData: DataRecord[] = [];
241.4     111 |
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/transformProps.ts:110:26
241.4 TS2304: Cannot find name 'DataRecord'.
241.4     108 |   }, new Map<string, DataRecord[]>());
241.4     109 |
241.4   > 110 |   const transformedData: DataRecord[] = [];
241.4         |                          ^^^^^^^^^^
241.4     111 |
241.4     112 |   if (breakdown) {
241.4     113 |     groupedData.forEach((value, key) => {
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/transformProps.ts:154:5
241.4 TS2339: Property 'width' does not exist on type 'EchartsWaterfallChartProps'.
241.4     152 | ): WaterfallChartTransformedProps {
241.4     153 |   const {
241.4   > 154 |     width,
241.4         |     ^^^^^
241.4     155 |     height,
241.4     156 |     formData,
241.4     157 |     legendState,
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/transformProps.ts:155:5
241.4 TS2339: Property 'height' does not exist on type 'EchartsWaterfallChartProps'.
241.4     153 |   const {
241.4     154 |     width,
241.4   > 155 |     height,
241.4         |     ^^^^^^
241.4     156 |     formData,
241.4     157 |     legendState,
241.4     158 |     queriesData,
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/transformProps.ts:157:5
241.4 TS2339: Property 'legendState' does not exist on type 'EchartsWaterfallChartProps'.
241.4     155 |     height,
241.4     156 |     formData,
241.4   > 157 |     legendState,
241.4         |     ^^^^^^^^^^^
241.4     158 |     queriesData,
241.4     159 |     hooks,
241.4     160 |     inContextMenu,
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/transformProps.ts:159:5
241.4 TS2339: Property 'hooks' does not exist on type 'EchartsWaterfallChartProps'.
241.4     157 |     legendState,
241.4     158 |     queriesData,
241.4   > 159 |     hooks,
241.4         |     ^^^^^
241.4     160 |     inContextMenu,
241.4     161 |   } = chartProps;
241.4     162 |   const refs: Refs = {};
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/transformProps.ts:160:5
241.4 TS2339: Property 'inContextMenu' does not exist on type 'EchartsWaterfallChartProps'.
241.4     158 |     queriesData,
241.4     159 |     hooks,
241.4   > 160 |     inContextMenu,
241.4         |     ^^^^^^^^^^^^^
241.4     161 |   } = chartProps;
241.4     162 |   const refs: Refs = {};
241.4     163 |   const { data = [] } = queriesData[0];
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/transformProps.ts:188:11
241.4 TS2304: Cannot find name 'CurrencyFormatter'.
241.4     186 |
241.4     187 |   const defaultFormatter = currencyFormat?.symbol
241.4   > 188 |     ? new CurrencyFormatter({ d3Format: yAxisFormat, currency: currencyFormat })
241.4         |           ^^^^^^^^^^^^^^^^^
241.4     189 |     : getNumberFormatter(yAxisFormat);
241.4     190 |
241.4     191 |   const seriesformatter = (params: ICallbackDataParams) => {
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/transformProps.ts:189:7
241.4 TS2304: Cannot find name 'getNumberFormatter'.
241.4     187 |   const defaultFormatter = currencyFormat?.symbol
241.4     188 |     ? new CurrencyFormatter({ d3Format: yAxisFormat, currency: currencyFormat })
241.4   > 189 |     : getNumberFormatter(yAxisFormat);
241.4         |       ^^^^^^^^^^^^^^^^^^
241.4     190 |
241.4     191 |   const seriesformatter = (params: ICallbackDataParams) => {
241.4     192 |     const { data } = params;
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/transformProps.ts:196:24
241.4 TS2304: Cannot find name 'ensureIsArray'.
241.4     194 |     return defaultFormatter(originalValue as number);
241.4     195 |   };
241.4   > 196 |   const groupbyArray = ensureIsArray(groupby);
241.4         |                        ^^^^^^^^^^^^^
241.4     197 |   const breakdownColumn = groupbyArray.length ? groupbyArray[0] : undefined;
241.4     198 |   const breakdownName = isAdhocColumn(breakdownColumn)
241.4     199 |     ? breakdownColumn.label!
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/transformProps.ts:198:25
241.4 TS2304: Cannot find name 'isAdhocColumn'.
241.4     196 |   const groupbyArray = ensureIsArray(groupby);
241.4     197 |   const breakdownColumn = groupbyArray.length ? groupbyArray[0] : undefined;
241.4   > 198 |   const breakdownName = isAdhocColumn(breakdownColumn)
241.4         |                         ^^^^^^^^^^^^^
241.4     199 |     ? breakdownColumn.label!
241.4     200 |     : breakdownColumn;
241.4     201 |   const xAxisColumn = xAxis || granularitySqla;
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/transformProps.ts:202:21
241.4 TS2304: Cannot find name 'isAdhocColumn'.
241.4     200 |     : breakdownColumn;
241.4     201 |   const xAxisColumn = xAxis || granularitySqla;
241.4   > 202 |   const xAxisName = isAdhocColumn(xAxisColumn)
241.4         |                     ^^^^^^^^^^^^^
241.4     203 |     ? xAxisColumn.label!
241.4     204 |     : xAxisColumn;
241.4     205 |   const metricLabel = getMetricLabel(metric);
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/transformProps.ts:205:23
241.4 TS2304: Cannot find name 'getMetricLabel'.
241.4     203 |     ? xAxisColumn.label!
241.4     204 |     : xAxisColumn;
241.4   > 205 |   const metricLabel = getMetricLabel(metric);
241.4         |                       ^^^^^^^^^^^^^^
241.4     206 |
241.4     207 |   const transformedData = transformer({
241.4     208 |     data,
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/transformProps.ts:282:11
241.4 TS2304: Cannot find name 'rgbToHex'.
241.4     280 |     const color = oppositeSigns
241.4     281 |       ? value > 0
241.4   > 282 |         ? rgbToHex(increaseColor.r, increaseColor.g, increaseColor.b)
241.4         |           ^^^^^^^^
241.4     283 |         : rgbToHex(decreaseColor.r, decreaseColor.g, decreaseColor.b)
241.4     284 |       : 'transparent';
241.4     285 |
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/transformProps.ts:283:11
241.4 TS2304: Cannot find name 'rgbToHex'.
241.4     281 |       ? value > 0
241.4     282 |         ? rgbToHex(increaseColor.r, increaseColor.g, increaseColor.b)
241.4   > 283 |         : rgbToHex(decreaseColor.r, decreaseColor.g, decreaseColor.b)
241.4         |           ^^^^^^^^
241.4     284 |       : 'transparent';
241.4     285 |
241.4     286 |     let opacity = 1;
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/transformProps.ts:336:49
241.4 TS2304: Cannot find name 'GenericDataType'.
241.4     334 |       return TOTAL_MARK;
241.4     335 |     }
241.4   > 336 |     if (coltypeMapping[xAxisColumns[index]] === GenericDataType.Temporal) {
241.4         |                                                 ^^^^^^^^^^^^^^^
241.4     337 |       if (typeof value === 'string') {
241.4     338 |         return getTimeFormatter(xAxisTimeFormat)(Number.parseInt(value, 10));
241.4     339 |       }
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/transformProps.ts:338:16
241.4 TS2304: Cannot find name 'getTimeFormatter'.
241.4     336 |     if (coltypeMapping[xAxisColumns[index]] === GenericDataType.Temporal) {
241.4     337 |       if (typeof value === 'string') {
241.4   > 338 |         return getTimeFormatter(xAxisTimeFormat)(Number.parseInt(value, 10));
241.4         |                ^^^^^^^^^^^^^^^^
241.4     339 |       }
241.4     340 |       return getTimeFormatter(xAxisTimeFormat)(value);
241.4     341 |     }
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/transformProps.ts:340:14
241.4 TS2304: Cannot find name 'getTimeFormatter'.
241.4     338 |         return getTimeFormatter(xAxisTimeFormat)(Number.parseInt(value, 10));
241.4     339 |       }
241.4   > 340 |       return getTimeFormatter(xAxisTimeFormat)(value);
241.4         |              ^^^^^^^^^^^^^^^^
241.4     341 |     }
241.4     342 |     return String(value);
241.4     343 |   };
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/transformProps.ts:411:54
241.4 TS2304: Cannot find name 'rgbToHex'.
241.4     409 |         },
241.4     410 |         itemStyle: {
241.4   > 411 |           color: formData.fallingOrder ? '#28a745' : rgbToHex(increaseColor.r, increaseColor.g, increaseColor.b),
241.4         |                                                      ^^^^^^^^
241.4     412 |         },
241.4     413 |         data: increaseData,
241.4     414 |       },
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/transformProps.ts:424:54
241.4 TS2304: Cannot find name 'rgbToHex'.
241.4     422 |         },
241.4     423 |         itemStyle: {
241.4   > 424 |           color: formData.fallingOrder ? '#28a745' : rgbToHex(decreaseColor.r, decreaseColor.g, decreaseColor.b),
241.4         |                                                      ^^^^^^^^
241.4     425 |         },
241.4     426 |         data: decreaseData,
241.4     427 |       },
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/transformProps.ts:437:54
241.4 TS2304: Cannot find name 'rgbToHex'.
241.4     435 |         },
241.4     436 |         itemStyle: {
241.4   > 437 |           color: formData.fallingOrder ? '#28a745' : rgbToHex(decreaseColor.r, decreaseColor.g, decreaseColor.b),
241.4         |                                                      ^^^^^^^^
241.4     438 |         },
241.4     439 |         data: totalData,
241.4     440 |       },
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/types.ts:20:8
241.4 TS1141: String literal expected.
241.4     18 |  */
241.4     19 | import {
241.4   > 20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
241.4        |        ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
241.4     21 |   ChartDataResponseResult,
241.4     22 |   ChartProps,
241.4     23 |   QueryFormColumn,
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/types.ts:20:118
241.4 TS2304: Cannot find name 'from'.
241.4     18 |  */
241.4     19 | import {
241.4   > 20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
241.4        |                                                                                                                      ^^^^
241.4     21 |   ChartDataResponseResult,
241.4     22 |   ChartProps,
241.4     23 |   QueryFormColumn,
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/types.ts:21:3
241.4 TS2304: Cannot find name 'ChartDataResponseResult'.
241.4     19 | import {
241.4     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
241.4   > 21 |   ChartDataResponseResult,
241.4        |   ^^^^^^^^^^^^^^^^^^^^^^^
241.4     22 |   ChartProps,
241.4     23 |   QueryFormColumn,
241.4     24 |   QueryFormData,
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/types.ts:21:3
241.4 TS2695: Left side of comma operator is unused and has no side effects.
241.4     19 | import {
241.4     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
241.4   > 21 |   ChartDataResponseResult,
241.4        |   ^^^^^^^^^^^^^^^^^^^^^^^
241.4     22 |   ChartProps,
241.4     23 |   QueryFormColumn,
241.4     24 |   QueryFormData,
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/types.ts:21:3
241.4 TS2695: Left side of comma operator is unused and has no side effects.
241.4     19 | import {
241.4     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
241.4   > 21 |   ChartDataResponseResult,
241.4        |   ^^^^^^^^^^^^^^^^^^^^^^^^
241.4   > 22 |   ChartProps,
241.4        | ^^^^^^^^^^^^^
241.4     23 |   QueryFormColumn,
241.4     24 |   QueryFormData,
241.4     25 |   QueryFormMetric,
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/types.ts:21:3
241.4 TS2695: Left side of comma operator is unused and has no side effects.
241.4     19 | import {
241.4     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
241.4   > 21 |   ChartDataResponseResult,
241.4        |   ^^^^^^^^^^^^^^^^^^^^^^^^
241.4   > 22 |   ChartProps,
241.4        | ^^^^^^^^^^^^^
241.4   > 23 |   QueryFormColumn,
241.4        | ^^^^^^^^^^^^^^^^^^
241.4     24 |   QueryFormData,
241.4     25 |   QueryFormMetric,
241.4     26 |   RgbaColor,
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/types.ts:21:3
241.4 TS2695: Left side of comma operator is unused and has no side effects.
241.4     19 | import {
241.4     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
241.4   > 21 |   ChartDataResponseResult,
241.4        |   ^^^^^^^^^^^^^^^^^^^^^^^^
241.4   > 22 |   ChartProps,
241.4        | ^^^^^^^^^^^^^
241.4   > 23 |   QueryFormColumn,
241.4        | ^^^^^^^^^^^^^
241.4   > 24 |   QueryFormData,
241.4        | ^^^^^^^^^^^^^^^^
241.4     25 |   QueryFormMetric,
241.4     26 |   RgbaColor,
241.4     27 | } from '@superset-ui/core';
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/types.ts:21:3
241.4 TS2695: Left side of comma operator is unused and has no side effects.
241.4     19 | import {
241.4     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
241.4   > 21 |   ChartDataResponseResult,
241.4        |   ^^^^^^^^^^^^^^^^^^^^^^^^
241.4   > 22 |   ChartProps,
241.4        | ^^^^^^^^^^^^^
241.4   > 23 |   QueryFormColumn,
241.4        | ^^^^^^^^^^^^^
241.4   > 24 |   QueryFormData,
241.4        | ^^^^^^^^^^^^^
241.4   > 25 |   QueryFormMetric,
241.4        | ^^^^^^^^^^^^^^^^^^
241.4     26 |   RgbaColor,
241.4     27 | } from '@superset-ui/core';
241.4     28 | import type { BarDataItemOption } from 'echarts/types/src/chart/bar/BarSeries';
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/types.ts:21:3
241.4 TS2695: Left side of comma operator is unused and has no side effects.
241.4     19 | import {
241.4     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
241.4   > 21 |   ChartDataResponseResult,
241.4        |   ^^^^^^^^^^^^^^^^^^^^^^^^
241.4   > 22 |   ChartProps,
241.4        | ^^^^^^^^^^^^^
241.4   > 23 |   QueryFormColumn,
241.4        | ^^^^^^^^^^^^^
241.4   > 24 |   QueryFormData,
241.4        | ^^^^^^^^^^^^^
241.4   > 25 |   QueryFormMetric,
241.4        | ^^^^^^^^^^^^^
241.4   > 26 |   RgbaColor,
241.4        | ^^^^^^^^^^^^
241.4     27 | } from '@superset-ui/core';
241.4     28 | import type { BarDataItemOption } from 'echarts/types/src/chart/bar/BarSeries';
241.4     29 | import type { CallbackDataParams } from 'echarts/types/src/util/types';
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/types.ts:22:3
241.4 TS2304: Cannot find name 'ChartProps'.
241.4     20 | import { GenericDataType, QueryFormData, QueryFormMetric, QueryFormColumn, Metric, AnnotationResult, SMART_DATE_ID } from '../types/local-compat';
241.4     21 |   ChartDataResponseResult,
241.4   > 22 |   ChartProps,
241.4        |   ^^^^^^^^^^
241.4     23 |   QueryFormColumn,
241.4     24 |   QueryFormData,
241.4     25 |   QueryFormMetric,
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/types.ts:23:3
241.4 TS2304: Cannot find name 'QueryFormColumn'.
241.4     21 |   ChartDataResponseResult,
241.4     22 |   ChartProps,
241.4   > 23 |   QueryFormColumn,
241.4        |   ^^^^^^^^^^^^^^^
241.4     24 |   QueryFormData,
241.4     25 |   QueryFormMetric,
241.4     26 |   RgbaColor,
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/types.ts:24:3
241.4 TS2304: Cannot find name 'QueryFormData'.
241.4     22 |   ChartProps,
241.4     23 |   QueryFormColumn,
241.4   > 24 |   QueryFormData,
241.4        |   ^^^^^^^^^^^^^
241.4     25 |   QueryFormMetric,
241.4     26 |   RgbaColor,
241.4     27 | } from '@superset-ui/core';
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/types.ts:25:3
241.4 TS2304: Cannot find name 'QueryFormMetric'.
241.4     23 |   QueryFormColumn,
241.4     24 |   QueryFormData,
241.4   > 25 |   QueryFormMetric,
241.4        |   ^^^^^^^^^^^^^^^
241.4     26 |   RgbaColor,
241.4     27 | } from '@superset-ui/core';
241.4     28 | import type { BarDataItemOption } from 'echarts/types/src/chart/bar/BarSeries';
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/types.ts:26:3
241.4 TS2304: Cannot find name 'RgbaColor'.
241.4     24 |   QueryFormData,
241.4     25 |   QueryFormMetric,
241.4   > 26 |   RgbaColor,
241.4        |   ^^^^^^^^^
241.4     27 | } from '@superset-ui/core';
241.4     28 | import type { BarDataItemOption } from 'echarts/types/src/chart/bar/BarSeries';
241.4     29 | import type { CallbackDataParams } from 'echarts/types/src/util/types';
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/types.ts:27:3
241.4 TS2304: Cannot find name 'from'.
241.4     25 |   QueryFormMetric,
241.4     26 |   RgbaColor,
241.4   > 27 | } from '@superset-ui/core';
241.4        |   ^^^^
241.4     28 | import type { BarDataItemOption } from 'echarts/types/src/chart/bar/BarSeries';
241.4     29 | import type { CallbackDataParams } from 'echarts/types/src/util/types';
241.4     30 | import { BaseTransformedProps, LegendFormData } from '../types';
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/types.ts:49:40
241.4 TS2304: Cannot find name 'QueryFormData'.
241.4     47 | };
241.4     48 |
241.4   > 49 | export type EchartsWaterfallFormData = QueryFormData &
241.4        |                                        ^^^^^^^^^^^^^
241.4     50 |   LegendFormData & {
241.4     51 |     increaseColor: RgbaColor;
241.4     52 |     decreaseColor: RgbaColor;
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/types.ts:51:20
241.4 TS2304: Cannot find name 'RgbaColor'.
241.4     49 | export type EchartsWaterfallFormData = QueryFormData &
241.4     50 |   LegendFormData & {
241.4   > 51 |     increaseColor: RgbaColor;
241.4        |                    ^^^^^^^^^
241.4     52 |     decreaseColor: RgbaColor;
241.4     53 |     totalColor: RgbaColor;
241.4     54 |     metric: QueryFormMetric;
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/types.ts:52:20
241.4 TS2304: Cannot find name 'RgbaColor'.
241.4     50 |   LegendFormData & {
241.4     51 |     increaseColor: RgbaColor;
241.4   > 52 |     decreaseColor: RgbaColor;
241.4        |                    ^^^^^^^^^
241.4     53 |     totalColor: RgbaColor;
241.4     54 |     metric: QueryFormMetric;
241.4     55 |     xAxis: QueryFormColumn;
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/types.ts:53:17
241.4 TS2304: Cannot find name 'RgbaColor'.
241.4     51 |     increaseColor: RgbaColor;
241.4     52 |     decreaseColor: RgbaColor;
241.4   > 53 |     totalColor: RgbaColor;
241.4        |                 ^^^^^^^^^
241.4     54 |     metric: QueryFormMetric;
241.4     55 |     xAxis: QueryFormColumn;
241.4     56 |     xAxisLabel: string;
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/types.ts:54:13
241.4 TS2304: Cannot find name 'QueryFormMetric'.
241.4     52 |     decreaseColor: RgbaColor;
241.4     53 |     totalColor: RgbaColor;
241.4   > 54 |     metric: QueryFormMetric;
241.4        |             ^^^^^^^^^^^^^^^
241.4     55 |     xAxis: QueryFormColumn;
241.4     56 |     xAxisLabel: string;
241.4     57 |     xAxisTimeFormat?: string;
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/types.ts:55:12
241.4 TS2304: Cannot find name 'QueryFormColumn'.
241.4     53 |     totalColor: RgbaColor;
241.4     54 |     metric: QueryFormMetric;
241.4   > 55 |     xAxis: QueryFormColumn;
241.4        |            ^^^^^^^^^^^^^^^
241.4     56 |     xAxisLabel: string;
241.4     57 |     xAxisTimeFormat?: string;
241.4     58 |     xTicksLayout?: WaterfallFormXTicksLayout;
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/types.ts:67:53
241.4 TS2304: Cannot find name 'ChartProps'.
241.4     65 | };
241.4     66 |
241.4   > 67 | export interface EchartsWaterfallChartProps extends ChartProps {
241.4        |                                                     ^^^^^^^^^^
241.4     68 |   formData: EchartsWaterfallFormData;
241.4     69 |   queriesData: ChartDataResponseResult[];
241.4     70 | }
241.4
241.4 ERROR in ./plugins/plugin-chart-echarts/src/Waterfall/types.ts:69:16
241.4 TS2304: Cannot find name 'ChartDataResponseResult'.
241.4     67 | export interface EchartsWaterfallChartProps extends ChartProps {
241.4     68 |   formData: EchartsWaterfallFormData;
241.4   > 69 |   queriesData: ChartDataResponseResult[];
241.4        |                ^^^^^^^^^^^^^^^^^^^^^^^
241.4     70 | }
241.4     71 |
241.4     72 | export type WaterfallChartTransformedProps =
241.4
241.4 webpack 5.99.9 compiled with 1414 errors in 219192 ms
------
target superset-init: failed to solve: process "/bin/sh -c if [ \"${DEV_MODE}\" = \"false\" ]; then       echo \"Running 'npm run ${BUILD_CMD}'\";       npm run ${BUILD_CMD};     else       echo \"Skipping 'npm run ${BUILD_CMD}' in dev mode\";     fi" did not complete successfully: exit code: 1

root@EC03-INS-LHUB01:/home/CORP/re_priyanshug1/ss/superset#
