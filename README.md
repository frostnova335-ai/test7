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
    { label: 'YTD', value: 'CUSTOM' },
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
