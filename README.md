console.log('DOWNLOAD START');

const response = await SupersetClient.post({
  endpoint: `/api/v1/dashboard/${dashboardId}/download_data`,
  body: JSON.stringify({
    export_type: exportType,
  }),
  parseMethod: undefined,
});

console.log('RESPONSE:', response);
console.log('STATUS:', response.status);
console.log('OK:', response.ok);
