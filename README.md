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
import { useState, useEffect } from 'react';
import { styled, css, useTheme } from '@superset-ui/core';
import { debounce } from 'lodash';
import { getUrlParam } from 'src/utils/urlUtils';
import { MainNav, MenuMode } from '@superset-ui/core/components/Menu';
import { Tooltip, Grid, Row, Col, Image } from '@superset-ui/core/components';
import { GenericLink } from 'src/components';
import { NavLink, useLocation } from 'react-router-dom';
import { Typography } from '@superset-ui/core/components/Typography';
import { useUiConfig } from 'src/components/UiConfigContext';
import { URL_PARAMS } from 'src/constants';
import {
  MenuObjectChildProps,
  MenuObjectProps,
  MenuData,
} from 'src/types/bootstrapTypes';
import RightMenu from './RightMenu';

const relabel = (label?: string) =>
  label === 'Dashboards' ? 'Home' : label || '';

interface MenuProps {
  data: MenuData;
  isFrontendRoute?: (path?: string) => boolean;
}

const StyledHeader = styled.header`
  ${({ theme }) => `
      font-family: 'Poppins', sans-serif;
      background: #E6F6FB;
      border-bottom: 1px solid rgba(0, 79, 112, 0.15);
      z-index: 10;

      &:nth-last-of-type(2) nav {
        margin-bottom: 2px;
      }
      .caret {
        display: none;
      }
      & .ant-image{
        display: contents;
        height: 100%;
        padding: ${theme.sizeUnit}px
          ${theme.sizeUnit * 2}px
          ${theme.sizeUnit}px
          ${theme.sizeUnit * 4}px;
      }
      .navbar-brand {
        display: flex;
        flex-direction: column;
        justify-content: center;
        /* must be exactly the height of the Antd navbar */
        min-height: 50px;
        padding: ${theme.sizeUnit}px
          ${theme.sizeUnit * 2}px
          ${theme.sizeUnit}px
          ${theme.sizeUnit * 6}px; /* Increased left padding */
        max-width: ${theme.sizeUnit * theme.brandIconMaxWidth}px;
        img {
          height: 100%;
          object-fit: contain;
        }
        &:focus {
          border-color: transparent;
        }
        &:focus-visible {
          border-color: ${theme.colorPrimaryText};
        }
      }
      .navbar-brand-text {
        border-left: 1px solid rgba(0, 79, 112, 0.2);
        border-right: 1px solid rgba(0, 79, 112, 0.2);
        height: 100%;
        color: #004F70;
        padding-left: ${theme.sizeUnit * 4}px;
        padding-right: ${theme.sizeUnit * 4}px;
        margin-right: ${theme.sizeUnit * 6}px;
        font-family: 'Poppins', sans-serif;
        font-size: 16px;
        font-weight: 600;
        float: left;
        display: flex;
        flex-direction: column;
        justify-content: center;

        span {
          max-width: ${theme.sizeUnit * 58}px;
          white-space: nowrap;
          overflow: hidden;
          text-overflow: ellipsis;
        }
        @media (max-width: 1127px) {
          display: none;
        }
      }
      .main-nav {
        font-family: 'Poppins', sans-serif;
        font-size: 16px;
        display: flex;
        justify-content: flex-end;
        align-items: center;
        background: transparent !important;
        
        .ant-menu {
          background: transparent !important;
          border: none !important;
        }
        
        .ant-menu-item,
        .ant-menu-submenu-title {
          color: #004F70 !important; /* Blue color for navigation */
          font-family: 'Poppins', sans-serif;
          font-size: 16px;
          font-weight: 500;
          text-align: right;
          background: transparent !important;
          
          &:hover,
          &.ant-menu-submenu-active {
            color: #004F70 !important;
            background-color: rgba(221, 238, 245, 0.7) !important;
          }
          
          a {
            color: #004F70 !important; /* Blue color for navigation */
            font-family: 'Poppins', sans-serif;
            font-size: 16px;
            font-weight: 500;
            text-align: right;
            
            &:hover {
              color: #004F70 !important;
            }
          }
        }

        /* Active menu item styling - bold blue */
        .ant-menu-item-selected,
        .ant-menu-submenu-selected > .ant-menu-submenu-title {
          font-weight: 700 !important;
          color: #004F70 !important; /* Bold blue for selected */
          
          a {
            font-weight: 700 !important;
            color: #004F70 !important;
          }
        }
        
        /* Remove icon from SQL submenu when it has no children or is not a submenu */
        .ant-menu-submenu-title {
          .anticon-caret-down {
            display: none !important;
          }
        }
        
        /* Make InsightsViews bold when on dashboard list page - handled via selectedKeys */
      }
      /* Ensure icons/carets follow navy palette in light header */
      svg {
        color: #004F70;
        fill: #004F70;
      }
      @media (max-width: 767px) {
        .navbar-brand {
          float: none;
        }
      }
      @media (max-width: 767px) {
        .ant-menu-item {
          padding: 0 ${theme.sizeUnit * 6}px 0
            ${theme.sizeUnit * 3}px !important;
        }
        .ant-menu > .ant-menu-item > span > a {
          padding: 0px;
        }
        .main-nav .ant-menu-submenu-title > svg:nth-of-type(1) {
          display: none;
        }
      }
  `}
`;
const { SubMenu } = MainNav;

const StyledSubMenu = styled(SubMenu)`
  /* Hide caret icon in submenu title */
  .ant-menu-submenu-title .anticon {
    display: none !important;
  }
  ${({ theme }) => css`
    [data-icon="caret-down"] {
      color: ${theme.colorIcon};
      font-size: ${theme.fontSizeXS}px;
      margin-left: ${theme.sizeUnit}px;
    }
    &.ant-menu-submenu {
        padding: ${theme.sizeUnit * 2}px ${theme.sizeUnit * 4}px;
        display: flex;
        align-items: center;
        height: 100%;  &.ant-menu-submenu-active {
    .ant-menu-title-content {
      color: ${theme.colorPrimary};
    }
  }
  `}
`;
const { useBreakpoint } = Grid;

export function Menu({
  data: {
    menu,
    brand,
    navbar_right: navbarRight,
    settings,
    environment_tag: environmentTag,
  },
  isFrontendRoute = () => false,
}: MenuProps) {
  const [showMenu, setMenu] = useState<MenuMode>('horizontal');
  const screens = useBreakpoint();
  const uiConfig = useUiConfig();
  const theme = useTheme();

  useEffect(() => {
    function handleResize() {
      if (window.innerWidth <= 767) {
        setMenu('inline');
      } else setMenu('horizontal');
    }
    handleResize();
    const windowResize = debounce(() => handleResize(), 10);
    window.addEventListener('resize', windowResize);
    return () => window.removeEventListener('resize', windowResize);
  }, []);

  enum Paths {
    Explore = '/explore',
    Dashboard = '/dashboard',
    Chart = '/chart',
    Datasets = '/tablemodelview',
  }

  const defaultTabSelection: string[] = [];
  const [activeTabs, setActiveTabs] = useState(defaultTabSelection);
  const location = useLocation();
  useEffect(() => {
    let cancelled = false;
    const path = location.pathname;
    
    const updateTabs = () => {
      if (cancelled) return;
      
      switch (true) {
        case path.startsWith('/insightshub/welcome') ||
          path.startsWith(Paths.Dashboard) ||
          path.includes('/dashboard/list/'):
          // When on home (welcome) or dashboard list, mark Dashboards as active (label is 'InsightsViews')
          setActiveTabs(['Dashboards']);
          break;
        case path.startsWith(Paths.Chart) || path.startsWith(Paths.Explore):
          setActiveTabs(['Charts']);
          break;
        case path.startsWith(Paths.Datasets):
          setActiveTabs(['Datasets']);
          break;
        default:
          setActiveTabs(defaultTabSelection);
      }
    };
    
    updateTabs();
    
    return () => {
      cancelled = true;
    };
  }, [location.pathname]);

  const standalone = getUrlParam(URL_PARAMS.standalone);
  if (standalone || uiConfig.hideNav) return <></>;

  const renderSubMenu = ({
    label,
    name,
    childs,
    url,
    index,
    isFrontendRoute,
  }: MenuObjectProps) => {
    // Use name as key for matching with activeTabs (name is the original key, label is relabeled for display)
    // For Dashboards, name is 'Dashboards' but label is 'InsightsViews' after relabeling
    const menuKey = name || label;
    if (url && isFrontendRoute) {
      return (
        <MainNav.Item key={menuKey} role="presentation">
          <NavLink role="button" to={url} activeClassName="is-active">
            {label}
          </NavLink>
        </MainNav.Item>
      );
    }
    if (url) {
      return (
        <MainNav.Item key={menuKey}>
          <Typography.Link href={url}>{label}</Typography.Link>
        </MainNav.Item>
      );
    }
    return (
      <StyledSubMenu
        key={menuKey}
        title={label}
        icon={<></>} /* Remove icon */
      >
        {childs?.map((child: MenuObjectChildProps | string, index1: number) => {
          if (typeof child === 'string' && child === '-' && label !== 'Data') {
            return <MainNav.Divider key={`$${index1}`} />;
          }
          if (typeof child !== 'string') {
            return (
              <MainNav.Item key={`${child.label}`}>
                {child.isFrontendRoute ? (
                  <NavLink
                    to={child.url || ''}
                    exact
                    activeClassName="is-active"
                  >
                    {child.label}
                  </NavLink>
                ) : (
                  <Typography.Link href={child.url}>
                    {child.label}
                  </Typography.Link>
                )}
              </MainNav.Item>
            );
          }
          return null;
        })}
      </StyledSubMenu>
    );
  };
  const renderBrand = () => {
    let link;
    if (theme.brandLogoUrl) {
      let style = { padding: '0px', margin: '0px' } as React.CSSProperties;
      if (theme.brandLogoHeight) {
        style = { ...style, height: theme.brandLogoHeight, minHeight: '0px' };
      }
      if (theme.brandLogoMargin) {
        style = { ...style, margin: theme.brandLogoMargin };
      }
      link = (
        <Typography.Link
          href={theme.brandLogoHref}
          className="navbar-brand"
          style={style}
        >
          <Image
            preview={false}
            src={theme.brandLogoUrl}
            alt={theme.brandLogoAlt || 'Apache Superset'}
          />
        </Typography.Link>
      );
    } else if (isFrontendRoute(window.location.pathname)) {
      // ---------------------------------------------------------------------------------
      // TODO: deprecate this once Theme is fully rolled out
      // Kept as is for backwards compatibility with the old theme system / superset_config.py
      link = (
        <GenericLink className="navbar-brand" to={brand.path}>
          <Image preview={false} src={brand.icon} alt={brand.alt} />
        </GenericLink>
      );
    } else {
      link = (
        <Typography.Link
          className="navbar-brand"
          href={brand.path}
          tabIndex={-1}
        >
          <Image preview={false} src={brand.icon} alt={brand.alt} />
        </Typography.Link>
      );
    }
    // ---------------------------------------------------------------------------------
    return <>{link}</>;
  };
  return (
    <StyledHeader className="top" id="main-menu" role="navigation">
      <Row>
        <Col md={6} xs={24} style={{ display: 'flex' }}>
          <Tooltip
            id="brand-tooltip"
            placement="bottomLeft"
            title={brand.tooltip}
            arrow={{ pointAtCenter: true }}
          >
            {renderBrand()}
          </Tooltip>
          {brand.text && (
            <div className="navbar-brand-text">
              <span>{brand.text}</span>
            </div>
          )}
        </Col>
        <Col
          md={18}
          xs={24}
          style={{
            display: 'flex',
            justifyContent: 'flex-end',
            alignItems: 'center',
            paddingRight: '24px',
          }}
        >
          <MainNav
            mode={showMenu}
            data-test="navbar-top"
            className="main-nav"
            selectedKeys={activeTabs}
            disabledOverflow
          >
            {menu.map((item, index) => {
              // Preserve original name for key matching, but use relabeled for display
              const originalName = item.name;
              // InsightsViews (Dashboards) nav item goes to home/welcome page
              const isDashboards = originalName === 'Dashboards';
              const resolvedUrl = isDashboards
                ? '/insightshub/welcome/'
                : item.url;
              const props = {
                index,
                ...item,
                url: resolvedUrl,
                label: relabel(item.label || item.name),
                name: originalName, // Keep original name for key matching
                isFrontendRoute: isFrontendRoute(resolvedUrl),
                // Clear children for Dashboards to force direct link instead of submenu
                childs: isDashboards
                  ? undefined
                  : item.childs?.map(c => {
                      if (typeof c === 'string') {
                        return c;
                      }

                      return {
                        ...c,
                        label: relabel(c.label),
                        name: c.name, // Keep original name for key matching
                        isFrontendRoute: isFrontendRoute(c.url),
                      };
                    }),
              };

              return renderSubMenu(props);
            })}
          </MainNav>
          <RightMenu
            align={screens.md ? 'flex-end' : 'flex-start'}
            settings={settings}
            navbarRight={navbarRight}
            isFrontendRoute={isFrontendRoute}
            environmentTag={environmentTag}
          />
        </Col>
      </Row>
    </StyledHeader>
  );
}

// transform the menu data to reorganize components
export default function MenuWrapper({ data, ...rest }: MenuProps) {
  const newMenuData = {
    ...data,
  };
  // Menu items that should go into settings dropdown
  const settingsMenus = {
    Data: true,
    Security: true,
    Manage: true,
  };

  // Cycle through menu.menu to build out cleanedMenu and settings
  const cleanedMenu: MenuObjectProps[] = [];
  const settings: MenuObjectProps[] = [];
  newMenuData.menu.forEach((item: any) => {
    if (!item) {
      return;
    }

    const children: (MenuObjectProps | string)[] = [];
    const newItem = {
      ...item,
    };

    // Filter childs
    if (item.childs) {
      item.childs.forEach((child: MenuObjectChildProps | string) => {
        if (typeof child === 'string') {
          children.push(child);
        } else if ((child as MenuObjectChildProps).label) {
          children.push(child);
        }
      });

      newItem.childs = children;
    }

    if (!settingsMenus.hasOwnProperty(item.name)) {
      cleanedMenu.push(newItem);
    } else {
      settings.push(newItem);
    }
  });

  newMenuData.menu = cleanedMenu;
  newMenuData.settings = settings;

  return <Menu data={newMenuData} {...rest} />;
}
