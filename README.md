import { createGlobalStyle } from 'styled-components';

const GlobalStyleOverride = createGlobalStyle`
  header,
  header.top-nav,
  .top-nav,
  .Header,
  .ant-layout-header,
  .ant-layout-header::before,
  .ant-layout-header::after {
    border-bottom: none !important;
    box-shadow: none !important;
  }
`;
