console.log('===== DOWNLOAD DEBUG =====');
console.log('downloadQuery state:', downloadQuery);
console.log('jsonMetadata state:', jsonMetadata);



<Input.TextArea
  value={downloadQuery}
  onChange={e => {
    console.log('TEXTAREA VALUE:', e.target.value);
    onDownloadQueryChange(e.target.value);
  }}



  console.log(
  'Loaded download_query:',
  metadata?.download_query,
);

setDownloadQuery(metadata?.download_query || '');
