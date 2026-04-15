import { t } from '@apache-superset/core/translation';
import { FrameComponentProps } from '../types';
import DatePicker from 'antd/es/date-picker';
import { useState } from 'react';

export function CurrentCalendarFrame({ onChange, value }: FrameComponentProps) {
  const { RangePicker } = DatePicker;

  const [showCalendar, setShowCalendar] = useState(false);

  const options = [
    { label: '7D', value: 'Last 7 days' },
    { label: '30D', value: 'Last 30 days' },
    { label: '90D', value: 'Last 90 days' },
    { label: 'ALL', value: 'CUSTOM' },
  ];

  const handleClick = (val: string) => {
    if (val === 'CUSTOM') {
      setShowCalendar(true);
    } else {
      setShowCalendar(false);
      onChange(val);
    }
  };

  return (
    <>
      <div className="section-title">{t('Quick Select')}</div>
      <div
        style={{
          display: 'inline-flex',
          background: '#f1f5f9',
          borderRadius: '12px',
          padding: '4px',
          gap: '4px',
        }}
      >
        {options.map(opt => (
          <div
            key={opt.value}
            onClick={() => handleClick(opt.value)}
            style={{
              padding: '6px 14px',
              borderRadius: '8px',
              cursor: 'pointer',
              fontWeight: 500,
              fontSize: '13px',
              transition: 'all 0.2s ease',
              background:
                value === opt.value || (opt.value === 'CUSTOM' && showCalendar)
                  ? '#ffffff'
                  : 'transparent',
              boxShadow:
                value === opt.value || (opt.value === 'CUSTOM' && showCalendar)
                  ? '0 1px 3px rgba(0,0,0,0.1)'
                  : 'none',
              color:
                value === opt.value || (opt.value === 'CUSTOM' && showCalendar)
                  ? '#0f172a'
                  : '#64748b',
            }}
          >
            {opt.label}
          </div>
        ))}
      </div>

      {showCalendar && (
        <div style={{ marginTop: '16px' }}>
          <div className="section-title">{t('Select Date Range')}</div>

          <RangePicker
            style={{ width: '100%' }}
            onChange={(dates: any, dateStrings: [string, string]) => {
              if (dateStrings[0] && dateStrings[1]) {
                onChange(`${dateStrings[0]} : ${dateStrings[1]}`);
              }
            }}
          />
        </div>
      )}
    </>
  );
}





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
import { ReactNode, useState, useEffect, useMemo } from 'react';
import { t } from '@apache-superset/core/translation';
import {
  NO_TIME_RANGE,
  useCSSTextTruncation,
  fetchTimeRange,
} from '@superset-ui/core';
import {
  css,
  styled,
  useTheme,
  SupersetTheme,
} from '@apache-superset/core/theme';
import {
  Button,
  Constants,
  Divider,
  Tooltip,
  Select,
} from '@superset-ui/core/components';
import ControlHeader from 'src/explore/components/ControlHeader';
import { Icons } from '@superset-ui/core/components/Icons';
import { useDebouncedEffect } from 'src/explore/exploreUtils';
import { noOp } from 'src/utils/common';
import ControlPopover from '../ControlPopover/ControlPopover';

import { DateFilterControlProps, FrameType } from './types';
import {
  DateFilterTestKey,
  FRAME_OPTIONS,
  guessFrame,
  useDefaultTimeFilter,
} from './utils';
import {
  CommonFrame,
  CalendarFrame,
  CustomFrame,
  AdvancedFrame,
  DateLabel,
} from './components';
import { CurrentCalendarFrame } from './components/CurrentCalendarFrame';


const ContentStyleWrapper = styled.div`
  ${({ theme }) => css`
    .ant-row {
      margin-top: 8px;
    }

    .ant-picker {
      padding: 4px 17px 4px;
      border-radius: 4px;
    }

    .ant-divider-horizontal {
      margin: 16px 0;
    }

    .control-label {
      font-size: ${theme.fontSizeSM}px;
      line-height: 16px;
      margin: 8px 0;
    }

    .section-title {
      font-style: normal;
      font-weight: ${theme.fontWeightStrong};
      font-size: 15px;
      line-height: 24px;
      margin-bottom: 8px;
    }

    .control-anchor-to {
      margin-top: 16px;
    }

    .control-anchor-to-datetime {
      width: 217px;
    }

    .footer {
      text-align: right;
    }
  `}
`;

const IconWrapper = styled.span`
  span {
    margin-right: ${({ theme }) => 2 * theme.sizeUnit}px;
    vertical-align: middle;
  }
  .text {
    vertical-align: middle;
  }
  .error {
    color: ${({ theme }) => theme.colorError};
  }
`;

const getTooltipTitle = (
  isLabelTruncated: boolean,
  label: string | undefined,
  range: string | undefined,
) =>
  isLabelTruncated ? (
    <div>
      {label && <strong>{label}</strong>}
      {range && (
        <div
          css={(theme: SupersetTheme) => css`
            margin-top: ${theme.sizeUnit}px;
          `}
        >
          {range}
        </div>
      )}
    </div>
  ) : (
    range || null
  );

export default function DateFilterLabel(props: DateFilterControlProps) {
  const {
    name,
    onChange,
    onOpenPopover = noOp,
    onClosePopover = noOp,
    isOverflowingFilterBar = false,
  } = props;
  const defaultTimeFilter = useDefaultTimeFilter();

  const value = props.value ?? defaultTimeFilter;
  const [actualTimeRange, setActualTimeRange] = useState<string>(value);

  const [show, setShow] = useState<boolean>(false);
  const guessedFrame = useMemo(() => guessFrame(value), [value]);
  const [frame, setFrame] = useState<FrameType>(guessedFrame);
  const [lastFetchedTimeRange, setLastFetchedTimeRange] = useState(value);
  const [timeRangeValue, setTimeRangeValue] = useState(value);
  const [validTimeRange, setValidTimeRange] = useState<boolean>(false);
  const [evalResponse, setEvalResponse] = useState<string>(value);
  const [tooltipTitle, setTooltipTitle] = useState<ReactNode | null>(value);
  const theme = useTheme();
  const [labelRef, labelIsTruncated] = useCSSTextTruncation<HTMLSpanElement>();

  useEffect(() => {
    if (value === NO_TIME_RANGE) {
      setActualTimeRange(NO_TIME_RANGE);
      setTooltipTitle(null);
      setValidTimeRange(true);
      return;
    }
    fetchTimeRange(value).then(({ value: actualRange, error }) => {
      if (error) {
        setEvalResponse(error || '');
        setValidTimeRange(false);
        setTooltipTitle(value || null);
      } else {
        /*
          HRT == human readable text
          ADR == actual datetime range
          +--------------+------+----------+--------+----------+-----------+
          |              | Last | Previous | Custom | Advanced | No Filter |
          +--------------+------+----------+--------+----------+-----------+
          | control pill | HRT  | HRT      | ADR    | ADR      |   HRT     |
          +--------------+------+----------+--------+----------+-----------+
          | tooltip      | ADR  | ADR      | HRT    | HRT      |   ADR     |
          +--------------+------+----------+--------+----------+-----------+
        */
        if (
          guessedFrame === 'Common' ||
          guessedFrame === 'Calendar' ||
          guessedFrame === 'Current' ||
          guessedFrame === 'No filter'
        ) {
          let displayValue = actualRange || value;

          const match = displayValue.match(
            /(\d{4}-\d{2}-\d{2}).+?(\d{4}-\d{2}-\d{2})/,
          );

          if (match) {
            displayValue = `${match[1]} to ${match[2]}`;
          }

          setActualTimeRange(displayValue);

          setTooltipTitle(
            getTooltipTitle(labelIsTruncated, displayValue, actualRange),
          );
        } else {
          setActualTimeRange(actualRange || '');

          setTooltipTitle(
            getTooltipTitle(labelIsTruncated, actualRange, value),
          );
        }
        setValidTimeRange(true);
      }
      setLastFetchedTimeRange(value);
      setEvalResponse(actualRange || value);
    });
  }, [guessedFrame, labelIsTruncated, labelRef, value]);

  useDebouncedEffect(
    () => {
      if (timeRangeValue === NO_TIME_RANGE) {
        setEvalResponse(NO_TIME_RANGE);
        setLastFetchedTimeRange(NO_TIME_RANGE);
        setValidTimeRange(true);
        return;
      }
      if (lastFetchedTimeRange !== timeRangeValue) {
        fetchTimeRange(timeRangeValue).then(({ value: actualRange, error }) => {
          if (error) {
            setEvalResponse(error || '');
            setValidTimeRange(false);
          } else {
            setEvalResponse(actualRange || '');
            setValidTimeRange(true);
          }
          setLastFetchedTimeRange(timeRangeValue);
        });
      }
    },
    Constants.SLOW_DEBOUNCE,
    [timeRangeValue],
  );

  function onSave() {
    onChange(timeRangeValue);
    setShow(false);
    onClosePopover();
  }


  function onOpen() {
    setTimeRangeValue(value);
    setFrame('Current');
    setShow(true);
    onOpenPopover();
  }

  function onHide() {
    setTimeRangeValue(value);
    setFrame(guessedFrame);
    setShow(false);
    onClosePopover();
  }

  const toggleOverlay = () => {
    if (show) {
      onHide();
    } else {
      onOpen();
    }
  };



  const overlayContent = (
    <ContentStyleWrapper>
      <CurrentCalendarFrame
        value={timeRangeValue}
        onChange={(val) => {
          setTimeRangeValue(val);
          onChange(val);
        }}
      />
    </ContentStyleWrapper>
  );

  const popoverContent = (
    <ControlPopover
      autoAdjustOverflow={false}
      trigger="click"
      placement="right"
      content={overlayContent}
      title={
        <IconWrapper>
          <Icons.EditOutlined />
          <span className="text">{t('Edit time range')}</span>
        </IconWrapper>
      }
      defaultOpen={show}
      open={show}
      onOpenChange={toggleOverlay}
      overlayStyle={{ width: '600px' }}
      destroyTooltipOnHide
      getPopupContainer={nodeTrigger =>
        isOverflowingFilterBar
          ? (nodeTrigger.parentNode as HTMLElement)
          : document.body
      }
      overlayClassName="time-range-popover"
    >
      <Tooltip placement="top" title={tooltipTitle}>
        <DateLabel
          name={name}
          aria-labelledby={`filter-name-${props.name}`}
          aria-describedby={`date-label-${props.name}`}
          label={actualTimeRange}
          isActive={show}
          isPlaceholder={actualTimeRange === NO_TIME_RANGE}
          data-test={DateFilterTestKey.PopoverOverlay}
          ref={labelRef}
        />
      </Tooltip>
    </ControlPopover>
  );

  return (
    <>
      <ControlHeader {...props} />
      {popoverContent}
    </>
  );
}




