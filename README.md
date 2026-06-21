{
  "download_query": "SELECT * FROM audio_csv LIMIT 100",
  "chart_configuration": {},
  "global_chart_configuration": {
    "scope": {"rootPath": ["ROOT_ID"], "excluded": []},
    "chartsInScope": []
  },
  "color_scheme": "",
  "refresh_frequency": 0,
  "expanded_slices": {},
  "label_colors": {},
  "timed_refresh_immune_slices": [],
  "cross_filters_enabled": true,
  "default_filters": "{}"
}
  "chart_configuration": {},
  "global_chart_configuration": {
    "scope": {"rootPath": ["ROOT_ID"], "excluded": []},
    "chartsInScope": [142, 143, 195]
  },
  "color_scheme": "",
  "refresh_frequency": 0,
  "expanded_slices": {},
  "label_colors": {},
  "timed_refresh_immune_slices": [],
  "cross_filters_enabled": true,
  "default_filters": "{}",
  "native_filter_configuration": [
    {
      "id": "NATIVE_FILTER-re27oF1C9ksZkGvKclOI-",
      "controlValues": {"enableEmptyFilter": false},
      "name": "Select date",
      "filterType": "filter_time",
      "targets": [{}],
      "defaultDataMask": {
        "extraFormData": {},
        "filterState": {},
        "ownState": {}
      },
      "cascadeParentIds": [],
      "scope": {"excluded": [142], "rootPath": ["ROOT_ID"]},
      "type": "NATIVE_FILTER",
      "description": "",
      "chartsInScope": [143, 42, 55, 93],
      "tabsInScope": ["TAB-y7_NMENli43nxGQwj1stW"]
    },
    {
      "id": "NATIVE_FILTER-HgoXN6-uAc_2X9uyw3NVa",
      "controlValues": {
        "enableEmptyFilter": false,
        "defaultToFirstItem": false,
        "creatable": true,
        "multiSelect": true,
        "searchAllOptions": false,
        "inverseSelection": false
      },
      "name": "Audio name",
      "filterType": "filter_select",
      "targets": [{"datasetId": 77, "column": {"name": "audio_name"}}],
      "defaultDataMask": {
        "extraFormData": {},
        "filterState": {},
        "ownState": {}
      },
      "cascadeParentIds": [],
      "scope": {"rootPath": ["ROOT_ID"], "excluded": [143]},
      "type": "NATIVE_FILTER",
      "description": "",
      "chartsInScope": [142],
      "tabsInScope": []
    },
    {
      "id": "NATIVE_FILTER-LRToVW0F3pwkoviVdSnJc",
      "controlValues": {
        "enableEmptyFilter": false,
        "defaultToFirstItem": false,
        "creatable": true,
        "multiSelect": true,
        "searchAllOptions": false,
        "inverseSelection": false
      },
      "name": "date",
      "filterType": "filter_select",
      "targets": [{"datasetId": 78, "column": {"name": "created_at"}}],
      "defaultDataMask": {
        "extraFormData": {},
        "filterState": {},
        "ownState": {}
      },
      "cascadeParentIds": [],
      "scope": {"rootPath": ["ROOT_ID"], "excluded": [42, 55, 93, 142]},
      "type": "NATIVE_FILTER",
      "description": "",
      "chartsInScope": [143],
      "tabsInScope": ["TAB-y7_NMENli43nxGQwj1stW"]
    }
  ],
  "filter_bar_orientation": "HORIZONTAL"
}
