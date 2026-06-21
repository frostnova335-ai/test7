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
import { useMemo } from 'react';
import { isFeatureEnabled, FeatureFlag, t } from '@superset-ui/core';
import { AsyncSelect } from '@superset-ui/core/components';
import { type TagType } from 'src/components';
import { loadTags } from 'src/components/Tag/utils';
import getOwnerName from 'src/utils/getOwnerName';
import Owner from 'src/types/Owner';
import { ModalFormField } from 'src/components/Modal';
import { useAccessOptions } from '../hooks/useAccessOptions';

type Roles = { id: number; name: string }[];
type Owners = {
  id: number;
  full_name?: string;
  first_name?: string;
  last_name?: string;
}[];

interface AccessSectionProps {
  isLoading: boolean;
  owners: Owners;
  roles: Roles;
  tags: TagType[];
  onChangeOwners: (owners: { value: number; label: string }[]) => void;
  onChangeRoles: (roles: { value: number; label: string }[]) => void;
  onChangeTags: (tags: { label: string; value: number }[]) => void;
  onClearTags: () => void;
}

const AccessSection = ({
  isLoading,
  owners,
  roles,
  tags,
  onChangeOwners,
  onChangeRoles,
  onChangeTags,
  onClearTags,
}: AccessSectionProps) => {
  const { loadAccessOptions } = useAccessOptions();

  const ownersSelectValue = useMemo(
    () =>
      (owners || []).map((owner: Owner) => ({
        value: owner.id,
        label: getOwnerName(owner),
      })),
    [owners],
  );

  const rolesSelectValue = useMemo(
    () =>
      (roles || []).map((role: { id: number; name: string }) => ({
        value: role.id,
        label: `${role.name}`,
      })),
    [roles],
  );

  const tagsAsSelectValues = useMemo(
    () =>
      tags.map((tag: { id: number; name: string }) => ({
        value: tag.id,
        label: tag.name,
      })),
    [tags],
  );

  return (
    <>
      <ModalFormField
        label={t('Owners')}
        testId="dashboard-owners-field"
        helperText={t(
          'Owners is a list of users who can alter the dashboard. Searchable by name or username.',
        )}
      >
        <AsyncSelect
          data-test="dashboard-owners-select"
          allowClear
          ariaLabel={t('Owners')}
          disabled={isLoading}
          mode="multiple"
          onChange={onChangeOwners}
          options={(input, page, pageSize) =>
            loadAccessOptions('owners', input, page, pageSize)
          }
          value={ownersSelectValue}
          showSearch
          placeholder={t('Search owners')}
        />
      </ModalFormField>
      {isFeatureEnabled(FeatureFlag.DashboardRbac) && (
        <ModalFormField
          label={t('Roles')}
          testId="dashboard-roles-field"
          helperText={t(
            'Roles is a list which defines access to the dashboard. Granting a role access to a dashboard will bypass dataset level checks. If no roles are defined, regular access permissions apply.',
          )}
          bottomSpacing={!isFeatureEnabled(FeatureFlag.TaggingSystem)}
        >
          <AsyncSelect
            data-test="dashboard-roles-select"
            allowClear
            ariaLabel={t('Roles')}
            disabled={isLoading}
            mode="multiple"
            onChange={onChangeRoles}
            options={(input, page, pageSize) =>
              loadAccessOptions('roles', input, page, pageSize)
            }
            value={rolesSelectValue}
            showSearch
            placeholder={t('Search roles')}
          />
        </ModalFormField>
      )}
      {isFeatureEnabled(FeatureFlag.TaggingSystem) && (
        <ModalFormField
          label={t('Tags')}
          testId="dashboard-tags-field"
          helperText={t(
            'A list of tags that have been applied to this dashboard.',
          )}
          bottomSpacing={false}
        >
          <AsyncSelect
            data-test="dashboard-tags-select"
            ariaLabel="Tags"
            mode="multiple"
            value={tagsAsSelectValues}
            options={loadTags}
            onChange={onChangeTags}
            onClear={onClearTags}
            allowClear
            showSearch
            placeholder={t('Search tags')}
          />
        </ModalFormField>
      )}
    </>
  );
};

export default AccessSection;







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
import { t, styled } from '@superset-ui/core';
import { JsonEditor } from '@superset-ui/core/components';
import { ModalFormField } from 'src/components/Modal';
import { ValidationObject } from 'src/components/Modal/useModalValidation';

const StyledJsonEditor = styled(JsonEditor)`
  /* Border is already applied by AceEditor itself */
`;

interface AdvancedSectionProps {
  jsonMetadata: string;
  jsonAnnotations: any[];
  validationStatus: ValidationObject;
  onJsonMetadataChange: (value: string) => void;
}

const AdvancedSection = ({
  jsonMetadata,
  jsonAnnotations,
  validationStatus,
  onJsonMetadataChange,
}: AdvancedSectionProps) => (
  <ModalFormField
    label={t('JSON Metadata')}
    testId="dashboard-metadata-field"
    helperText={t(
      'This JSON object is generated dynamically when clicking the save ' +
        'or overwrite button in the dashboard view. It is exposed here for ' +
        'reference and for power users who may want to alter specific parameters.',
    )}
    error={
      validationStatus.advanced?.hasErrors && jsonAnnotations.length > 0
        ? t('Invalid JSON metadata')
        : undefined
    }
    bottomSpacing={false}
  >
    <StyledJsonEditor
      data-test="dashboard-metadata-editor"
      showLoadingForImport
      name="json_metadata"
      value={jsonMetadata}
      onChange={onJsonMetadataChange}
      tabSize={2}
      width="100%"
      height="200px"
      wrapEnabled
      annotations={jsonAnnotations}
    />
  </ModalFormField>
);

export default AdvancedSection;






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
import { css, SupersetTheme, t } from '@superset-ui/core';
import {
  FormItem,
  Input,
  FormInstance,
  Select,
} from '@superset-ui/core/components';
import { ModalFormField } from 'src/components/Modal';
import { ValidationObject } from 'src/components/Modal/useModalValidation';
import { DASHBOARD_CATEGORIES } from 'src/dashboard/constants/categories';

interface BasicInfoSectionProps {
  form: FormInstance;
  validationStatus: ValidationObject;
}

const categorySelectStyle = (theme: SupersetTheme) => css`
  width: 100%;
  min-width: ${theme.sizeUnit * 44}px;
  max-width: 100%;
  display: block;

  .ant-select-selector {
    width: 100%;
  }
`;

const BasicInfoSection = ({
  form,
  validationStatus,
}: BasicInfoSectionProps) => {
  const titleValue = form.getFieldValue('title');
  const categoryValue = form.getFieldValue('category');
  const hasTitleError =
    validationStatus.basic?.hasErrors &&
    (!titleValue || titleValue.trim().length === 0);
  const hasCategoryError =
    validationStatus.basic?.hasErrors && !categoryValue;

  return (
    <>
      <ModalFormField
        label={t('Name')}
        required
        testId="dashboard-name-field"
        error={hasTitleError ? t('Dashboard name is required') : undefined}
      >
        <FormItem
          name="title"
          noStyle
          rules={[
            {
              required: true,
              message: t('Dashboard name is required'),
              whitespace: true,
            },
          ]}
        >
          <Input
            placeholder={t('The display name of your dashboard')}
            data-test="dashboard-title-input"
            type="text"
          />
        </FormItem>
      </ModalFormField>
      <ModalFormField
        label={t('Category')}
        required
        testId="dashboard-category-field"
        error={hasCategoryError ? t('Dashboard category is required') : undefined}
      >
        <FormItem
          name="category"
          noStyle
          rules={[
            {
              required: true,
              message: t('Dashboard category is required'),
            },
          ]}
        >
          <Select
            css={categorySelectStyle}
            placeholder={t('Select')}
            data-test="dashboard-category-select"
            allowClear
            options={DASHBOARD_CATEGORIES.map(category => ({
              value: category,
              label: category,
            }))}
            // Ensure category order matches Home page (no alphabetical re-sorting)
            filterSort={(a, b) =>
              DASHBOARD_CATEGORIES.indexOf(String((a as any).value)) -
              DASHBOARD_CATEGORIES.indexOf(String((b as any).value))
            }
          />
        </FormItem>
      </ModalFormField>
      <ModalFormField
        label={t('URL Slug')}
        testId="dashboard-slug-field"
        bottomSpacing={false}
      >
        <FormItem name="slug" noStyle>
          <Input
            placeholder={t('A readable URL for your dashboard')}
            data-test="dashboard-slug-input"
            type="text"
          />
        </FormItem>
      </ModalFormField>
    </>
  );
};

export default BasicInfoSection;





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

export { default as BasicInfoSection } from './BasicInfoSection';
export { default as AccessSection } from './AccessSection';
export { default as StylingSection } from './StylingSection';
export { default as RefreshSection } from './RefreshSection';
export { default as CertificationSection } from './CertificationSection';
export { default as AdvancedSection } from './AdvancedSection';
