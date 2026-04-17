/**
 * Licensed to the Apache Software Foundation (ASF) under one
 * or more contributor license agreements.  See the NOTICE file
 * distributed with this work for additional information
 * regarding copyright ownership.  The ASF licenses this file
 * to you under the Apache License, Version 2.0
 */

import { ClientErrorObject, SupersetError } from '@superset-ui/core';
import { FC } from 'react';
import { useChartOwnerNames } from 'src/hooks/apiResources';
import { ErrorMessageWithStackTrace } from 'src/components';
import { ChartSource } from 'src/types/ChartSource';

export type Props = {
  chartId: number;
  error?: SupersetError;
  subtitle: React.ReactNode;
  link?: string;
  source: ChartSource;
  stackTrace?: string;
} & Omit<ClientErrorObject, 'error'>;

const DEFAULT_CHART_ERROR = 'Unable to Load Chart';

const getFriendlyChartError = (error?: SupersetError) => {
  const msg = (error?.message || '').toLowerCase();

  if (
    msg.includes('missing dataset') ||
    msg.includes('dataset associated') ||
    msg.includes('no longer exists')
  ) {
    return 'This chart is temporarily unavailable.';
  }

  if (
    msg.includes('column') ||
    msg.includes('missing in dataset') ||
    msg.includes('does not exist')
  ) {
    return 'Some required data is unavailable for the selected filters.';
  }

  if (msg.includes('network')) {
    return 'Unable to fetch data right now. Please try again later.';
  }

  if (msg.includes('timeout')) {
    return 'Request timed out. Please narrow your filters and try again.';
  }

  return 'This chart cannot be displayed right now.';
};

export const ChartErrorMessage: FC<Props> = ({
  chartId,
  error,
  ...props
}) => {
  const { result: owners } = useChartOwnerNames(chartId);

  const isExplorePage = window.location.pathname.includes('/explore');

  // DASHBOARD / APP VIEW → Friendly centered message only
  if (!isExplorePage) {
    return (
      <div
        style={{
          width: '100%',
          height: '100%',
          minHeight: 220,
          display: 'flex',
          alignItems: 'center',
          justifyContent: 'center',
          textAlign: 'center',
          fontSize: '15px',
          fontWeight: 500,
          color: '#666',
          padding: '20px',
        }}
      >
        {getFriendlyChartError(error)}
      </div>
    );
  }

  // EXPLORE VIEW → Full developer error
  const ownedError =
    error && {
      ...error,
      extra: {
        ...error.extra,
        owners,
      },
    };

  return (
    <ErrorMessageWithStackTrace
      {...props}
      error={ownedError}
      title={DEFAULT_CHART_ERROR}
      closable={false}
    />
  );
};
