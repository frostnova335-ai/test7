/**
 * Licensed to the Apache Software Foundation (ASF) under one
 * or more contributor license agreements.  See the NOTICE file
 * distributed with this work for additional information
 * regarding copyright ownership.  The ASF licenses this file
 * to you under the Apache License, Version 2.0 (the
 * "License"); you may not use this file except in compliance
 * with the License.  You may obtain a copy of the License at
 *
 *   http://www.apache.org/licenses/LICENSE-2.0
 *
 * Unless required by applicable law or agreed to in writing,
 * software distributed under the License is distributed on an
 * "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
 * KIND, either express or implied.  See the License for the
 * specific language governing permissions and limitations
 * under the License.
 */

import React, { useState } from 'react';
import { Button, Dropdown, Menu, notification } from 'antd';
import { DownloadOutlined } from '@ant-design/icons';
import { SupersetClient } from '@superset-ui/core';

const DashboardExportMenu = ({ dashboardId }) => {
  const [loading, setLoading] = useState(false);

  const handleExport = async (format) => {
    setLoading(true);
    try {
      const response = await SupersetClient.post({
        endpoint: `/api/v1/dashboards/${dashboardId}/export_data/?format=${format}`,
      });

      const blob = new Blob([response.data], {
        type: format === 'csv' ? 'text/csv' : 'application/vnd.openxmlformats-officedocument.spreadsheetml.sheet',
      });
      const url = window.URL.createObjectURL(blob);
      const link = document.createElement('a');
      link.href = url;
      link.download = `dashboard_${dashboardId}_${new Date().toISOString().split('T')[0]}.${format === 'csv' ? 'csv' : 'xlsx'}`;
      document.body.appendChild(link);
      link.click();
      document.body.removeChild(link);
      window.URL.revokeObjectURL(url);

      notification.success({
        message: 'Export Successful',
        description: `Dashboard exported as ${format.toUpperCase()}`,
      });
    } catch (error) {
      notification.error({
        message: 'Export Failed',
        description: 'Failed to export dashboard data',
      });
      console.error('Export error:', error);
    } finally {
      setLoading(false);
    }
  };

  const menu = (
    <Menu>
      <Menu.Item key="csv" onClick={() => handleExport('csv')}>
        Export to CSV
      </Menu.Item>
      <Menu.Item key="xlsx" onClick={() => handleExport('xlsx')}>
        Export to Excel
      </Menu.Item>
    </Menu>
  );

  return (
    <Dropdown overlay={menu} trigger={['click']}>
      <Button
        buttonStyle="secondary"
        className="action-button"
        disabled={loading}
        icon={<DownloadOutlined />}
        aria-label="Download dashboard"
        title="Download dashboard data"
      >
        {loading ? 'Exporting...' : 'Download'}
      </Button>
    </Dropdown>
  );
};

export default DashboardExportMenu;
