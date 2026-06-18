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



service "superset-init" didn't complete successfully: exit 1
root@EC03-B17-UBAPP1:/home/CORP/application/bu-digital-insightshub-backend# docker compose -f docker-compose-non-dev.yml logs superset-init --tail=300
superset_init  | Checking for stale uv lock files...
superset_init  | Installing superset-core in editable mode
superset_init  | Resolved 1 package in 2ms
superset_init  |    Building apache-superset-core @ file:///app/superset-core
superset_init  |       Built apache-superset-core @ file:///app/superset-core
superset_init  | Prepared 1 package in 1.23s
superset_init  | Uninstalled 1 package in 15ms
superset_init  | warning: Failed to hardlink files; falling back to full copy. This may lead to degraded performance.
superset_init  |          If the cache and target directories are on different filesystems, hardlinking may not be supported.
superset_init  |          If this is intentional, set `export UV_LINK_MODE=copy` or use `--link-mode=copy` to suppress this warning.
superset_init  | Installed 1 package in 6ms
superset_init  |  ~ apache-superset-core==0.0.1rc2 (from file:///app/superset-core)
superset_init  | Reinstalling the app in editable mode
superset_init  | Resolved 162 packages in 2.07s
superset_init  |    Building apache-superset @ file:///app
superset_init  |    Building apache-superset-core @ file:///app/superset-core
superset_init  |       Built apache-superset @ file:///app
superset_init  |       Built apache-superset-core @ file:///app/superset-core
superset_init  | Prepared 2 packages in 995ms
superset_init  | Uninstalled 2 packages in 13ms
superset_init  | warning: Failed to hardlink files; falling back to full copy. This may lead to degraded performance.
superset_init  |          If the cache and target directories are on different filesystems, hardlinking may not be supported.
superset_init  |          If this is intentional, set `export UV_LINK_MODE=copy` or use `--link-mode=copy` to suppress this warning.
superset_init  | Installed 2 packages in 10ms
superset_init  |  ~ apache-superset==1.0.7 (from file:///app)
superset_init  |  ~ apache-superset-core==0.0.1rc2 (from file:///app/superset-core)
superset_init  | Installing postgres requirements
superset_init  | Resolved 163 packages in 1.59s
superset_init  |    Building apache-superset @ file:///app
superset_init  |       Built apache-superset @ file:///app
superset_init  | Prepared 1 package in 844ms
superset_init  | Uninstalled 1 package in 1ms
superset_init  | warning: Failed to hardlink files; falling back to full copy. This may lead to degraded performance.
superset_init  |          If the cache and target directories are on different filesystems, hardlinking may not be supported.
superset_init  |          If this is intentional, set `export UV_LINK_MODE=copy` or use `--link-mode=copy` to suppress this warning.
superset_init  | Installed 1 package in 7ms
superset_init  |  ~ apache-superset==1.0.7 (from file:///app)
superset_init  | Skipping local overrides
superset_init  | Unknown Operation!!!
superset_init  | ######################################################################
superset_init  | Init Step 1/3 [Starting] -- Applying DB migrations
superset_init  | ######################################################################
superset_init  | Loaded your LOCAL configuration at [/app/pythonpath/superset_config.py]
superset_init  | 2026-06-18 11:37:04,845:INFO:alembic.runtime.migration:Context impl PostgresqlImpl.
superset_init  | 2026-06-18 11:37:04,845:INFO:alembic.runtime.migration:Will assume transactional DDL.
superset_init  | 2026-06-18 11:37:05,199:INFO:superset.app:Pending database migrations: run 'superset db upgrade'
superset_init  | 2026-06-18 11:37:05,254:ERROR:superset.app:Failed to create app
superset_init  | Traceback (most recent call last):
superset_init  |   File "/app/superset/app.py", line 75, in create_app
superset_init  |     app_initializer.init_app()
superset_init  |   File "/app/superset/initialization/__init__.py", line 771, in init_app
superset_init  |     self.init_app_in_ctx()
superset_init  |   File "/app/superset/initialization/__init__.py", line 642, in init_app_in_ctx
superset_init  |     self.init_views()
superset_init  |   File "/app/superset/initialization/__init__.py", line 165, in init_views
superset_init  |     from superset.dashboards.api import DashboardRestApi
superset_init  |   File "/app/superset/dashboards/api.py", line 24, in <module>
superset_init  |     from superset.commands.dashboard.export_data import ExportDashboardCommand
superset_init  |   File "/app/superset/commands/dashboard/export_data.py", line 4, in <module>
superset_init  |     from typing import tuple
superset_init  | ImportError: cannot import name 'tuple' from 'typing' (/usr/local/lib/python3.11/typing.py)
superset_init  | Traceback (most recent call last):
superset_init  |   File "/app/.venv/bin/superset", line 10, in <module>
superset_init  |     sys.exit(superset())
superset_init  |              ^^^^^^^^^^
superset_init  |   File "/app/.venv/lib/python3.11/site-packages/click/core.py", line 1442, in __call__
superset_init  |     return self.main(*args, **kwargs)
superset_init  |            ^^^^^^^^^^^^^^^^^^^^^^^^^^
superset_init  |   File "/app/.venv/lib/python3.11/site-packages/click/core.py", line 1363, in main
superset_init  |     rv = self.invoke(ctx)
superset_init  |          ^^^^^^^^^^^^^^^^
superset_init  |   File "/app/.venv/lib/python3.11/site-packages/click/core.py", line 1827, in invoke
superset_init  |     super().invoke(ctx)
superset_init  |   File "/app/.venv/lib/python3.11/site-packages/click/core.py", line 1226, in invoke
superset_init  |     return ctx.invoke(self.callback, **ctx.params)
superset_init  |            ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
superset_init  |   File "/app/.venv/lib/python3.11/site-packages/click/core.py", line 794, in invoke
superset_init  |     return callback(*args, **kwargs)
superset_init  |            ^^^^^^^^^^^^^^^^^^^^^^^^^
superset_init  |   File "/app/.venv/lib/python3.11/site-packages/click/decorators.py", line 34, in new_func
superset_init  |     return f(get_current_context(), *args, **kwargs)
superset_init  |            ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
superset_init  |   File "/app/.venv/lib/python3.11/site-packages/flask/cli.py", line 355, in decorator
superset_init  |     app = __ctx.ensure_object(ScriptInfo).load_app()
superset_init  |           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
superset_init  |   File "/app/.venv/lib/python3.11/site-packages/flask/cli.py", line 302, in load_app
superset_init  |     app = self.create_app()
superset_init  |           ^^^^^^^^^^^^^^^^^
superset_init  |   File "/app/superset/cli/main.py", line 52, in create_app
superset_init  |     return create_superset_app()
superset_init  |            ^^^^^^^^^^^^^^^^^^^^^
superset_init  |   File "/app/superset/app.py", line 75, in create_app
superset_init  |     app_initializer.init_app()
superset_init  |   File "/app/superset/initialization/__init__.py", line 771, in init_app
superset_init  |     self.init_app_in_ctx()
superset_init  |   File "/app/superset/initialization/__init__.py", line 642, in init_app_in_ctx
superset_init  |     self.init_views()
superset_init  |   File "/app/superset/initialization/__init__.py", line 165, in init_views
superset_init  |     from superset.dashboards.api import DashboardRestApi
superset_init  |   File "/app/superset/dashboards/api.py", line 24, in <module>
superset_init  |     from superset.commands.dashboard.export_data import ExportDashboardCommand
superset_init  |   File "/app/superset/commands/dashboard/export_data.py", line 4, in <module>
superset_init  |     from typing import tuple
superset_init  | ImportError: cannot import name 'tuple' from 'typing' (/usr/local/lib/python3.11/typing.py)
root




