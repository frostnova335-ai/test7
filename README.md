import { ControlPanelConfig } from '@superset-ui/chart-controls';

const config: ControlPanelConfig = {
  controlPanelSections: [
    {
      label: 'Audio Settings',
      expanded: true,
      controlSetRows: [
        [
          {
            name: 'audio_url_column',
            config: {
              type: 'SelectControl',
              label: 'Audio URL Column',
              default: 'audio_url',
              clearable: false,
              renderTrigger: false,
              mapStateToProps: ({ datasource }) => ({
                choices:
                  datasource?.columns?.map((col: any) => [
                    col.column_name,
                    col.column_name,
                  ]) || [],
              }),
            },
          },
        ],
        [
          {
            name: 'label_column',
            config: {
              type: 'SelectControl',
              label: 'Label Column',
              default: 'audio_name',
              clearable: false,
              renderTrigger: false,
              mapStateToProps: ({ datasource }) => ({
                choices:
                  datasource?.columns?.map((col: any) => [
                    col.column_name,
                    col.column_name,
                  ]) || [],
              }),
            },
          },
        ],
        [
          {
            name: 'gradient_start',
            config: {
              type: 'ColorPickerControl',
              label: 'Gradient Start',
              default: '#6366F1',
              renderTrigger: true,
            },
          },
          {
            name: 'gradient_end',
            config: {
              type: 'ColorPickerControl',
              label: 'Gradient End',
              default: '#8B5CF6',
              renderTrigger: true,
            },
          },
        ],
        [
          {
            name: 'row_limit',
            config: {
              type: 'TextControl',
              label: 'Number of Audios',
              default: 5,
              renderTrigger: false,
            },
          },
        ],
      ],
    },
  ],
};

export default config;
