"""Export dashboard data command."""
import io
from datetime import datetime
from typing import tuple

import pandas as pd
from openpyxl import Workbook
from openpyxl.styles import Font, PatternFill, Alignment

from superset.commands.base import BaseCommand
from superset.daos.dashboard import DashboardDAO
from superset.models.dashboard import Dashboard
from superset.errors import DashboardAccessDeniedError, DashboardNotFoundError


class ExportDashboardCommand(BaseCommand):
    """Export dashboard data to CSV or XLSX."""

    def __init__(
        self,
        dashboard_id: int | str,
        format_type: str = 'csv',
        user=None,
    ):
        self.dashboard_id = dashboard_id
        self.format_type = format_type
        self.user = user

    def run(self) -> tuple[io.BytesIO, str, str]:
        """
        Export dashboard data.
        
        Returns:
            tuple: (file_content, filename, mimetype)
        """
        dashboard = DashboardDAO.get_by_id_or_slug(self.dashboard_id)
        
        if not dashboard:
            raise DashboardNotFoundError()
        
        if not dashboard.can_access():
            raise DashboardAccessDeniedError()
        
        dashboard_name = dashboard.dashboard_title or 'dashboard'
        filename = f"{dashboard_name}_{datetime.now().strftime('%Y-%m-%d')}"
        
        data = self._get_dashboard_data(dashboard)
        
        if self.format_type == 'csv':
            return self._export_csv(data, filename)
        elif self.format_type == 'xlsx':
            return self._export_xlsx(data, filename)
        else:
            raise ValueError(f"Unsupported format: {self.format_type}")

    def _get_dashboard_data(self, dashboard: Dashboard) -> dict:
        """Get data from all charts in dashboard."""
        charts_data = {}
        
        for chart in dashboard.charts:
            try:
                chart_data = {
                    'title': chart.slice_name or f'Chart {chart.id}',
                    'data': self._fetch_chart_data(chart),
                }
                charts_data[chart.id] = chart_data
            except Exception as e:
                print(f"Error fetching data for chart {chart.id}: {e}")
                continue
        
        return charts_data

    def _fetch_chart_data(self, chart):
        """Fetch data from a specific chart."""
        try:
            data = chart.get_data()
            return data
        except Exception:
            return {}

    def _export_csv(
        self, data: dict, filename: str
    ) -> tuple[io.BytesIO, str, str]:
        """Export data as CSV."""
        all_data = []
        
        for chart_id, chart_info in data.items():
            if isinstance(chart_info['data'], dict):
                df = pd.DataFrame(chart_info['data'])
            else:
                df = pd.DataFrame(chart_info['data'])
            
            df.insert(0, 'Chart', chart_info['title'])
            all_data.append(df)
        
        result_df = pd.concat(all_data, ignore_index=True) if all_data else pd.DataFrame()
        
        output = io.BytesIO()
        result_df.to_csv(output, index=False)
        output.seek(0)
        
        return output, f"{filename}.csv", 'text/csv'

    def _export_xlsx(
        self, data: dict, filename: str
    ) -> tuple[io.BytesIO, str, str]:
        """Export data as XLSX with formatting."""
        output = io.BytesIO()
        workbook = Workbook()
        workbook.remove(workbook.active)
        
        for chart_id, chart_info in data.items():
            sheet = workbook.create_sheet(title=chart_info['title'][:31])
            
            if isinstance(chart_info['data'], dict):
                df = pd.DataFrame(chart_info['data'])
            else:
                df = pd.DataFrame(chart_info['data'])
            
            header_fill = PatternFill(start_color='366092', end_color='366092', fill_type='solid')
            header_font = Font(bold=True, color='FFFFFF')
            
            for col_idx, col_name in enumerate(df.columns, 1):
                cell = sheet.cell(row=1, column=col_idx)
                cell.value = col_name
                cell.fill = header_fill
                cell.font = header_font
                cell.alignment = Alignment(horizontal='center', vertical='center')
            
            for row_idx, row_data in enumerate(df.iterrows(), 2):
                for col_idx, value in enumerate(row_data[1], 1):
                    sheet.cell(row=row_idx, column=col_idx, value=value)
            
            for column in sheet.columns:
                max_length = 0
                column_letter = column[0].column_letter
                for cell in column:
                    try:
                        if len(str(cell.value)) > max_length:
                            max_length = len(str(cell.value))
                    except:
                        pass
                adjusted_width = (max_length + 2)
                sheet.column_dimensions[column_letter].width = adjusted_width
        
        workbook.save(output)
        output.seek(0)
        
        return output, f"{filename}.xlsx", 'application/vnd.openxmlformats-officedocument.spreadsheetml.sheet'
