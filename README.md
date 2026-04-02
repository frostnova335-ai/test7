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

import { t } from '@apache-superset/core/translation';
import { SupersetClient } from '@superset-ui/core';
import { styled, css } from '@apache-superset/core/theme';
import {
  Button,
  Card,
  Flex,
  Form,
  Input,
  Typography,
  Icons,
} from '@superset-ui/core/components';
import { useState, useEffect, useMemo } from 'react';
import { capitalize } from 'lodash/fp';
import { addDangerToast } from 'src/components/MessageToasts/actions';
import { useDispatch } from 'react-redux';
import getBootstrapData from 'src/utils/getBootstrapData';
// import leftSideLogin from 'src/assets/images/login_images/left-side-login.png';

/* ── Design tokens (InsightsHub premium design) ── */
const COLORS = {
  brandBlue: '#0A2540',
  brandBlueDark: '#1a3a5a',
  accentCyan: '#00D4FF',
  white: '#FFFFFF',
  slate300: '#cbd5e1',
  slate400: '#94a3b8',
  slate500: '#64748b',
  slate600: '#475569',
  slate700: '#334155',
} as const;

/* ── Captcha helpers ── */
const generateCaptcha = (): string => {
  const chars = 'ABCDEFGHJKLMNPQRSTUVWXYZ23456789';
  let result = '';
  for (let i = 0; i < 6; i += 1) {
    result += chars.charAt(Math.floor(Math.random() * chars.length));
  }
  return result;
};

const normalizeCaptcha = (value: string): string =>
  value.replace(/\s+/g, '').toUpperCase();

/* ── Types ── */
type OAuthProvider = { name: string; icon: string };
type OIDProvider = { name: string; url: string };
type Provider = OAuthProvider | OIDProvider;

interface LoginFormValues {
  username: string;
  password: string;
}

enum AuthType {
  AuthOID = 0,
  AuthDB = 1,
  AuthLDAP = 2,
  AuthOauth = 4,
}

/* ══════════════════════════════════════════════════════
   Styled Components — InsightsHub premium design
   ══════════════════════════════════════════════════════ */

const PageWrapper = styled.div`
  position: relative;
  width: 100%;
  min-height: 100dvh;
  display: flex;
  overflow-x: hidden;
  overflow-y: auto;
  font-family: 'Plus Jakarta Sans', 'Inter', -apple-system, BlinkMacSystemFont,
    sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

  @media (max-width: 1023px) {
    flex-direction: column;
  }
`;

/* ── LEFT PANEL: Mesh gradient + glass card ── */
const LeftPanel = styled.div`
  position: relative;
  width: 50%;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  overflow: hidden;
  background-color: ${COLORS.brandBlue};
  background-image: radial-gradient(
      at 0% 0%,
      hsla(210, 100%, 20%, 1) 0px,
      transparent 50%
    ),
    radial-gradient(
      at 100% 0%,
      hsla(190, 100%, 30%, 1) 0px,
      transparent 50%
    ),
    radial-gradient(
      at 100% 100%,
      hsla(200, 100%, 15%, 1) 0px,
      transparent 50%
    ),
    radial-gradient(
      at 0% 100%,
      hsla(215, 100%, 10%, 1) 0px,
      transparent 50%
    );

  &::after {
    content: '';
    position: absolute;
    inset: 0;
    background: rgba(10, 37, 64, 0.6);
    backdrop-filter: blur(1px);
    z-index: 1;
  }

  @media (max-width: 1023px) {
    display: none;
  }
`;

const GlowLayer = styled.div`
  position: absolute;
  inset: 0;
  opacity: 0.4;
  z-index: 2;
`;

const GlowOrb = styled.div<{
  top?: string;
  left?: string;
  bottom?: string;
  right?: string;
}>`
  position: absolute;
  width: 24rem;
  height: 24rem;
  border-radius: 9999px;
  filter: blur(120px);
  top: ${({ top }) => top ?? 'auto'};
  left: ${({ left }) => left ?? 'auto'};
  bottom: ${({ bottom }) => bottom ?? 'auto'};
  right: ${({ right }) => right ?? 'auto'};
`;

const GlassCard = styled.div`
  position: relative;
  z-index: 10;
  width: 100%;
  max-width: 40rem;
  margin: 0 4rem;
  padding: 2.75rem;
  background: rgba(255, 255, 255, 0.03);
  backdrop-filter: blur(12px);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 2rem;
  box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.25);
`;

const LiveTag = styled.div`
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.25rem 0.75rem;
  border-radius: 9999px;
  background: rgba(0, 212, 255, 0.1);
  border: 1px solid rgba(0, 212, 255, 0.2);
  margin-bottom: 2rem;
`;

const LiveDot = styled.span`
  position: relative;
  width: 8px;
  height: 8px;

  &::before {
    content: '';
    position: absolute;
    inset: 0;
    border-radius: 50%;
    background: ${COLORS.accentCyan};
    animation: ping 1.5s cubic-bezier(0, 0, 0.2, 1) infinite;
  }

  &::after {
    content: '';
    position: absolute;
    inset: 0;
    border-radius: 50%;
    background: ${COLORS.accentCyan};
  }

  @keyframes ping {
    75%,
    100% {
      transform: scale(2);
      opacity: 0;
    }
  }
`;

const LeftHeadline = styled.h2`
  font-size: 4.5rem;
  font-weight: 800;
  line-height: 1.1;
  letter-spacing: -0.025em;
  color: ${COLORS.white};
  margin: 0 0 1.5rem;

  @media (max-width: 1366px) {
    font-size: 3.5rem;
  }
`;

const GradientText = styled.span`
  background: linear-gradient(to right, ${COLORS.accentCyan}, #60a5fa);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
`;

const LeftDescription = styled.p`
  font-size: 1.125rem;
  font-weight: 500;
  color: rgba(203, 213, 225, 0.9);
  line-height: 1.625;
  margin: 0 0 2.5rem;
  max-width: 28rem;
`;

const StatsGrid = styled.div`
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1.5rem;
  padding-top: 1rem;
`;

const StatItem = styled.div`
  display: flex;
  flex-direction: column;
  gap: 0.25rem;
`;

const StatValue = styled.span`
  font-size: 1.5rem;
  font-weight: 700;
  color: ${COLORS.white};
`;

const StatLabel = styled.span`
  font-size: 0.75rem;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  color: ${COLORS.slate400};
`;

const LeftLogo = styled.div`
  position: absolute;
  bottom: 3rem;
  left: 4rem;
  z-index: 10;
  display: flex;
  align-items: center;
  gap: 1rem;
`;

const LogoIconBox = styled.div`
  width: 2.5rem;
  height: 2.5rem;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 0.75rem;
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(12px);
  border: 1px solid rgba(255, 255, 255, 0.2);
`;

const LogoText = styled.span`
  font-size: 1.25rem;
  font-weight: 700;
  letter-spacing: -0.05em;
  color: ${COLORS.white};
`;

/* ── RIGHT PANEL: Login form ── */
const RightPanel = styled.div`
  flex: 1;
  width: 50%;
  min-height: 100dvh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 1.5rem 3rem;
  background: linear-gradient(135deg, #f0f4f8 0%, #e2e8f0 100%);
  position: relative;
  overflow: hidden;

  &::before {
    content: '';
    position: absolute;
    width: 40%;
    height: 40%;
    background: radial-gradient(
      circle,
      rgba(0, 212, 255, 0.1) 0%,
      transparent 70%
    );
    top: 10%;
    right: 10%;
    z-index: 0;
  }

  @media (max-width: 1023px) {
    width: 100%;
    padding: 1.5rem;
  }

  @media (max-height: 820px) {
    justify-content: flex-start;
    padding-top: 1.25rem;
    padding-bottom: 1.25rem;
  }
`;

const GlassFormContainer = styled.div`
  position: relative;
  z-index: 10;
  width: 100%;
  max-width: 38rem;
  padding: 3rem 4rem;
  background: rgba(255, 255, 255, 0.7);
  backdrop-filter: blur(20px);
  border: 1px solid rgba(255, 255, 255, 0.8);
  border-radius: 2.5rem;
  box-shadow: 0 8px 32px 0 rgba(10, 37, 64, 0.08);

  @media (max-width: 640px) {
    padding: 2rem;
  }
`;

const MobileLogo = styled.div`
  display: flex;
  align-items: center;
  gap: 0.75rem;
  margin-bottom: 2.5rem;

  @media (min-width: 1024px) {
    display: none;
  }
`;

const MobileLogoIcon = styled.div`
  width: 2.5rem;
  height: 2.5rem;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 0.75rem;
  background: ${COLORS.brandBlue};
  color: ${COLORS.white};
`;

const FormHeading = styled.h1`
  font-size: 2rem;
  font-weight: 800;
  letter-spacing: -0.025em;
  color: ${COLORS.brandBlue};
  margin: 0 0 0.75rem;
  text-align: center;

  @media (min-width: 1024px) {
    text-align: left;
  }

  @media (max-width: 1366px) {
    font-size: 3rem;
  }
`;

const FormSubheading = styled.p`
  font-size: 1rem;
  font-weight: 500;
  color: ${COLORS.slate600};
  margin: 0 0 2.5rem;
  text-align: center;

  @media (min-width: 1024px) {
    text-align: left;
  }
`;

const FormLabel = styled.label`
  display: block;
  font-size: 0.75rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  color: ${COLORS.slate500};
  margin-bottom: 0.375rem;
`;

const InputWrapper = styled.div`
  position: relative;

 .ant-input {
  border-radius: 1.125rem !important;
  border: 1px solid rgba(255, 255, 255, 0.4) !important;
  background: rgba(255, 255, 255, 0.5) !important;
  backdrop-filter: blur(4px);
  padding: 1.05rem 3rem 1.05rem 3rem !important;
  font-size: 1rem !important;
  color: ${COLORS.brandBlue} !important;

  &:focus {
    border-color: ${COLORS.brandBlue} !important;
    background: rgba(255, 255, 255, 0.8) !important;
    box-shadow: 0 0 0 4px rgba(10, 37, 64, 0.05) !important;
  }

  &::placeholder {
    color: ${COLORS.slate400};
  }
}
  .ant-input-prefix {
    margin-right: 0.5rem;
    color: ${COLORS.slate400};
  }
`;

const InputIcon = styled.span`
  position: absolute;
  left: 1rem;
  top: 50%;
  transform: translateY(-50%);
  z-index: 1;
  color: ${COLORS.slate400};
  pointer-events: none;
`;

/* Captcha section - styled like "I am not a robot" box */
const CaptchaSection = styled.div`
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 1rem 1.25rem;
  border-radius: 1rem;
  border: 1px solid rgba(255, 255, 255, 0.4);
  background: rgba(255, 255, 255, 0.4);
  backdrop-filter: blur(4px);
  box-shadow: 0 1px 3px 0 rgba(0, 0, 0, 0.05);
  gap: 1rem;
`;

const CaptchaInputGroup = styled.div`
  display: flex;
  align-items: center;
  gap: 0.75rem;
  flex: 1;
  min-width: 0;
`;

const CaptchaInputStyled = styled(Input)`
  width: 29rem;
  height: 2.5rem !important;
  border-radius: 0.5rem !important;
  border: 1px solid rgba(255, 255, 255, 0.5) !important;
  background: rgba(255, 255, 255, 0.6) !important;
  font-size: 0.875rem !important;
  font-weight: 600 !important;
  letter-spacing: 0.1em !important;
  text-transform: uppercase !important;
  color: ${COLORS.brandBlue} !important;

  &:focus {
    border-color: ${COLORS.brandBlue} !important;
  }
`;

const CaptchaBox = styled.div`
  padding: 0 1rem;
  height: 2.5rem;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 0.5rem;
  background: ${COLORS.brandBlue};
  color: ${COLORS.white};
  font-size: 1rem;
  font-weight: 700;
  font-style: italic;
  letter-spacing: 0.25em;
  font-family: 'Courier New', monospace;
  min-width: 7.5rem;
  user-select: none;
`;

const RefreshBtn = styled.button`
  width: 2.5rem;
  height: 2.5rem;
  border: 1px solid rgba(255, 255, 255, 0.5);
  border-radius: 0.5rem;
  background: rgba(255, 255, 255, 0.6);
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.2s ease;

  &:hover {
    border-color: ${COLORS.brandBlue};
    background: rgba(255, 255, 255, 0.9);
  }
`;

const CaptchaIndicator = styled.div`
  flex-shrink: 0;
  color: ${COLORS.slate400};
`;

const LoginButton = styled(Button)`
  width: 100%;
  height: 3rem;
  border-radius: 1rem;
  font-size: 1.375rem;
  font-weight: 700;
  background: linear-gradient(to right, ${COLORS.brandBlue}, ${COLORS.brandBlueDark}) !important;
  border: none !important;
  box-shadow: 0 10px 15px -3px rgba(10, 37, 64, 0.2);
  transition: all 0.2s ease;

  &:hover {
    transform: scale(1.01);
    box-shadow: 0 20px 25px -5px rgba(10, 37, 64, 0.3) !important;
  }

  &:active {
    transform: scale(0.98);
  }
`;

const EnterpriseDivider = styled.div`
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
  margin-top: 3rem;
  margin-bottom: 1.5rem;
  width: 100%;
`;

const DividerLine = styled.div`
  width: 2rem;
  height: 1px;
  background: ${COLORS.slate300};
`;

const DividerText = styled.span`
  font-size: 0.625rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.2em;
  color: ${COLORS.slate500};
`;

const EnterpriseIcons = styled.div`
  display: flex;
  justify-content: center;
  gap: 1.5rem;
  color: ${COLORS.slate500};
  margin-bottom: 1.5rem;
  width: 100%;
`;

const TermsText = styled.p`
  font-size: 0.6875rem;
  text-align: center;
  color: ${COLORS.slate500};
  line-height: 1.5;
  max-width: 15rem;
  margin: 0 auto;
`;

const TermsLink = styled.a`
  color: ${COLORS.brandBlue};
  font-weight: 600;
  text-decoration: none;

  &:hover {
    text-decoration: underline;
  }
`;

const ForgotLink = styled.a`
  font-size: 0.75rem;
  font-weight: 700;
  color: ${COLORS.brandBlue};
  text-decoration: none;

  &:hover {
    text-decoration: underline;
  }
`;
const EyeIcon = styled.span`
  position: absolute;
  right: 1rem;
  top: 50%;
  transform: translateY(-50%);
  color: ${COLORS.slate400};
  cursor: pointer;
  z-index: 2;

  &:hover {
    color: ${COLORS.brandBlue};
  }
`;
const OAuthButton = styled(Button)`
  height: 2.75rem;
  border: 1px solid rgba(255, 255, 255, 0.5);
  border-radius: 1rem;
  font-size: 0.875rem;
  font-weight: 500;
  background: rgba(255, 255, 255, 0.6) !important;

  &:hover {
    border-color: ${COLORS.brandBlue};
    color: ${COLORS.brandBlue};
  }
`;

/* ══════════════════════════════════════════════════════
   Component
   ══════════════════════════════════════════════════════ */

export default function Login() {
  const [form] = Form.useForm<LoginFormValues>();
  const [isLoading, setIsLoading] = useState(false);
  const [showPassword, setShowPassword] = useState(false);
  const [captchaCode, setCaptchaCode] = useState<string>(generateCaptcha);
  const [userCaptchaInput, setUserCaptchaInput] = useState<string>('');
  const dispatch = useDispatch();

  const bootstrapData = getBootstrapData();
  const authType: AuthType = bootstrapData.common.conf.AUTH_TYPE;
  const providers: Provider[] = bootstrapData.common.conf.AUTH_PROVIDERS;

  useEffect(() => {
    const link = document.createElement('link');
    link.href =
      'https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@300;400;500;600;700;800&family=Inter:wght@400;500;600&display=swap';
    link.rel = 'stylesheet';
    document.head.appendChild(link);
    return () => {
      if (link.parentNode) link.parentNode.removeChild(link);
    };
  }, []);

  useEffect(() => {
    const loginAttempted = sessionStorage.getItem('login_attempted');

    if (loginAttempted === 'true') {
      sessionStorage.removeItem('login_attempted');
      dispatch(addDangerToast(t('Invalid username or password')));
      form.setFieldsValue({ password: '' });
    }
  }, [dispatch, form]);

  const handleFormSubmit = (values: LoginFormValues) => {
    const expectedCaptcha = normalizeCaptcha(captchaCode);
    const enteredCaptcha = normalizeCaptcha(userCaptchaInput);

    if (!enteredCaptcha || enteredCaptcha !== expectedCaptcha) {
      dispatch(addDangerToast(t('The verification code is incorrect.')));
      refreshCaptcha();
      return;
    }

    setIsLoading(true);
    sessionStorage.setItem('login_attempted', 'true');
    SupersetClient.postForm('/login/', values, '');
  };

  const refreshCaptcha = () => {
    setCaptchaCode(generateCaptcha());
    setUserCaptchaInput('');
  };

  const getProviderIcon = (
    providerName: string,
  ): React.JSX.Element | undefined => {
    if (!providerName || typeof providerName !== 'string') {
      return undefined;
    }
    const iconComponentName = `${capitalize(providerName)}Outlined`;
    const IconComponent = (Icons as Record<string, React.ComponentType<object>>)[
      iconComponentName
    ];

    if (IconComponent && typeof IconComponent === 'function') {
      return <IconComponent />;
    }
    return undefined;
  };

  const renderOAuthProviders = () => (
    <Flex justify="center" vertical gap="middle">
      <Form layout="vertical" requiredMark="optional" form={form}>
        {providers.map((provider: OAuthProvider | OIDProvider) => (
          <Form.Item key={provider.name}>
            <OAuthButton
              href={`/login/${provider.name}`}
              block
              iconPosition="start"
              icon={getProviderIcon(provider.name)}
            >
              {t('Sign in with')} {capitalize(provider.name)}
            </OAuthButton>
          </Form.Item>
        ))}
      </Form>
    </Flex>
  );

  const renderLoginForm = () => (
    <Form
      layout="vertical"
      requiredMark={false}
      form={form}
      onFinish={handleFormSubmit}
    >
      <Form.Item
        name="username"
        rules={[{ required: true, message: t('Please enter your username') }]}
        style={{ marginBottom: 24 }}
      >
        <div>
          <FormLabel>{t('Username')}</FormLabel>
          <InputWrapper>
            <InputIcon>
              <Icons.MailOutlined iconSize="m" />
            </InputIcon>
            <Input
              placeholder="Username"
              data-test="username-input"
              autoFocus
            />
          </InputWrapper>
        </div>
      </Form.Item>

      <Form.Item
        name="password"
        rules={[{ required: true, message: t('Please enter your password') }]}
        style={{ marginBottom: 24 }}
      >
        <div>
          <div
            style={{
              display: 'flex',
              alignItems: 'center',
              justifyContent: 'space-between',
              marginBottom: '0.375rem',
            }}
          >
            <FormLabel htmlFor="password">{t('Password')}</FormLabel>
            {/* <ForgotLink href="#">{t('Forgot?')}</ForgotLink> */}
          </div>
            <InputWrapper>
              <InputIcon>
                <Icons.LockOutlined iconSize="m" />
              </InputIcon>

              <Input
                type={showPassword ? 'text' : 'password'}
                placeholder="••••••••"
                data-test="password-input"
              />
               <EyeIcon onClick={() => setShowPassword(prev => !prev)}>
        {showPassword ? (
          <Icons.EyeInvisibleOutlined iconSize="m" />
        ) : (
          <Icons.EyeOutlined iconSize="m" />
        )}
      </EyeIcon>
            </InputWrapper>
          
        </div>
      </Form.Item>

      <Form.Item style={{ marginBottom: 24 }}>
        <CaptchaSection>
          <CaptchaInputGroup>
            <CaptchaInputStyled
              value={userCaptchaInput}
              onChange={e =>
                setUserCaptchaInput(e.target.value.toUpperCase().slice(0, 6))
              }
              placeholder={t('Enter Captcha')}
              data-test="captcha-input"
              maxLength={6}
            />
            <CaptchaBox>{captchaCode}</CaptchaBox>
            <RefreshBtn
              type="button"
              aria-label={t('Refresh captcha')}
              onClick={refreshCaptcha}
            >
              <Icons.ReloadOutlined iconSize="m" aria-hidden />
            </RefreshBtn>
          </CaptchaInputGroup>
          {/* <CaptchaIndicator>
            <Icons.CheckCircleOutlined iconSize="l" aria-hidden />
          </CaptchaIndicator> */}
        </CaptchaSection>
      </Form.Item>

      <Form.Item style={{ marginBottom: 0 }}>
        <LoginButton
          type="primary"
          htmlType="submit"
          loading={isLoading}
          data-test="login-button"
        >
          {t('Login')}
        </LoginButton>
      </Form.Item>
    </Form>
  );

  return (
    <PageWrapper data-test="login-form">
      {/* Left panel - desktop only */}
      <LeftPanel>
        <GlowLayer>
          <GlowOrb
            top="25%"
            left="25%"
            style={{ background: 'rgba(0, 212, 255, 0.2)' }}
          />
          <GlowOrb
            bottom="25%"
            right="25%"
            style={{ background: 'rgba(37, 99, 235, 0.2)' }}
          />
        </GlowLayer>
        <GlassCard>
          <LiveTag>
            <LiveDot />
            <span
              style={{
                fontSize: '10px',
                fontWeight: 700,
                textTransform: 'uppercase',
                letterSpacing: '0.1em',
                color: COLORS.accentCyan,
              }}
            >
              {t('Live Intelligence')}
            </span>
          </LiveTag>
          <LeftHeadline>
            {t('The Future of')} <br />
            <GradientText>{t('Contact Center Analytics')}</GradientText>
          </LeftHeadline>
          <LeftDescription>
            {t('Transform every conversation into actionable insight.')}
          </LeftDescription>
          <StatsGrid>
            <StatItem>
              <StatValue>99.9%</StatValue>
              <StatLabel>{t('Uptime Reliability')}</StatLabel>
            </StatItem>
            <StatItem>
              <StatValue>{t('Real-time')}</StatValue>
              <StatLabel>{t('Processing Latency')}</StatLabel>
            </StatItem>
          </StatsGrid>
        </GlassCard>
        <LeftLogo>
          <LogoIconBox>
            <Icons.DashboardOutlined
              iconSize="m"
              iconColor={COLORS.accentCyan}
            />
          </LogoIconBox>
          <LogoText>InsightsHub</LogoText>
        </LeftLogo>
      </LeftPanel>

      {/* Right panel - login form */}
      <RightPanel>
        <GlassFormContainer>
          <MobileLogo>
            <MobileLogoIcon>
              <Icons.DashboardOutlined iconSize="m" />
            </MobileLogoIcon>
            <LogoText>InsightsHub</LogoText>
          </MobileLogo>

          <FormHeading>{t('Welcome to InsightsHub')}</FormHeading>
          <FormSubheading>{t('Please enter your credentials')}</FormSubheading>

          {authType === AuthType.AuthOID && renderOAuthProviders()}
          {authType === AuthType.AuthOauth && renderOAuthProviders()}
          {(authType === AuthType.AuthDB || authType === AuthType.AuthLDAP) &&
            renderLoginForm()}

          <EnterpriseDivider>
            <DividerLine />
            <DividerText>{t('Enterprise Access')}</DividerText>
            <DividerLine />
          </EnterpriseDivider>
          <EnterpriseIcons>
            <Icons.KeyOutlined iconSize="xl" style={{ cursor: 'help' }} />
            <Icons.LockOutlined iconSize="xl" style={{ cursor: 'help' }} />
            <Icons.MonitorOutlined iconSize="xl" style={{ cursor: 'help' }} />
          </EnterpriseIcons>
          <TermsText>
            {t('By logging in, you agree to our')}{' '}
            <TermsLink href="#">{t('Terms of Service')}</TermsLink>{' '}
            {t('and')}{' '}
            <TermsLink href="#">{t('Privacy Policy')}</TermsLink>.
          </TermsText>
        </GlassFormContainer>
      </RightPanel>
    </PageWrapper>
  );
}

