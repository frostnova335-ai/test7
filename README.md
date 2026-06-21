import { SupersetClient } from '@superset-ui/core';


const downloadDashboardData = async (
  exportType: 'csv' | 'excel',
) => {
  try {
    const response = await SupersetClient.post({
      endpoint: `/api/v1/dashboard/${dashboardId}/download_data`,
      body: JSON.stringify({
        export_type: exportType,
      }),
      parseMethod: undefined,
      headers: {
        'Content-Type': 'application/json',
      },
    });

    const blob = await response.blob();

    const url = window.URL.createObjectURL(blob);

    const link = document.createElement('a');

    link.href = url;

    link.download =
      exportType === 'excel'
        ? `${dashboardTitle}.xlsx`
        : `${dashboardTitle}.csv`;

    document.body.appendChild(link);

    link.click();

    link.remove();

    window.URL.revokeObjectURL(url);
  } catch (error) {
    addDangerToast(t('Failed to download dashboard data'));
  }
};





DownloadDashboardCsv = 'download-dashboard-csv',
DownloadDashboardExcel = 'download-dashboard-excel',



case MenuKeys.DownloadDashboardCsv:
  downloadDashboardData('csv');
  break;

case MenuKeys.DownloadDashboardExcel:
  downloadDashboardData('excel');
  break;




  menuItems.push(downloadMenuItem);

menuItems.push({
  key: MenuKeys.DownloadDashboardCsv,
  label: t('Download Dashboard Data (CSV)'),
});

menuItems.push({
  key: MenuKeys.DownloadDashboardExcel,
  label: t('Download Dashboard Data (Excel)'),
});



