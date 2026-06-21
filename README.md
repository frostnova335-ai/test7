interface AdvancedSectionProps {
  jsonMetadata: string;
  jsonAnnotations: any[];
  validationStatus: ValidationObject;
  onJsonMetadataChange: (value: string) => void;
  downloadQuery: string;
  onDownloadQueryChange: (value: string) => void;
}


const AdvancedSection = ({
  jsonMetadata,
  jsonAnnotations,
  validationStatus,
  onJsonMetadataChange,
  downloadQuery,
  onDownloadQueryChange,
}: AdvancedSectionProps) => (



import { JsonEditor, Input } from '@superset-ui/core/components';


<ModalFormField
  label={t('Download Query')}
  testId="dashboard-download-query"
  helperText={t(
    'SQL query executed when users click the dashboard download button.',
  )}
>
  <Input.TextArea
    value={downloadQuery}
    onChange={e => onDownloadQueryChange(e.target.value)}
    rows={6}
    placeholder="SELECT * FROM my_table"
  />
</ModalFormField>




<AdvancedSection
  jsonMetadata={jsonMetadata}
  jsonAnnotations={jsonAnnotations}
  validationStatus={validationStatus}
  onJsonMetadataChange={setJsonMetadata}
  downloadQuery={downloadQuery}
  onDownloadQueryChange={setDownloadQuery}
/>


