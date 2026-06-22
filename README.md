const jsonMetadataObj = getJsonMetadata();

console.log('BEFORE ASSIGN:', jsonMetadataObj);

jsonMetadataObj.refresh_frequency = refreshFrequency;
jsonMetadataObj.download_query = downloadQuery;

console.log(
  'AFTER ASSIGN DOWNLOAD_QUERY:',
  jsonMetadataObj.download_query,
);

console.log(
  'FULL METADATA AFTER ASSIGN:',
  jsonMetadataObj,
);

const customLabelColors = jsonMetadataObj.label_colors || {};






console.log(
  'JSON SENT TO BACKEND:',
  currentJsonMetadata,
);





console.log(
  'DOWNLOAD QUERY BEFORE SAVE:',
  downloadQuery,
);

console.log(
  'CURRENT JSON METADATA BEFORE SAVE:',
  currentJsonMetadata,
);



console.log(
  'SAVE PAYLOAD:',
  JSON.stringify(saveData, null, 2),
);
