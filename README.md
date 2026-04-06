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
  Modal,
  Icons,
} from '@superset-ui/core/components';
import { useState, useEffect, useMemo } from 'react';
import { capitalize } from 'lodash/fp';
import { addDangerToast } from 'src/components/MessageToasts/actions';
import { useDispatch } from 'react-redux';
import getBootstrapData from 'src/utils/getBootstrapData';
// import leftSideLogin from 'src/assets/images/login_images/bg.png';

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
  height: 100dvh;
  min-height: 100dvh;
  display: flex;
  overflow-x: hidden;
  overflow-y: hidden;
  font-family: 'Plus Jakarta Sans', 'Inter', -apple-system, BlinkMacSystemFont,
    sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

  @media (max-width: 1023px) {
    flex-direction: column;
    overflow-y: auto;
  }
`;

/* ── LEFT PANEL: Mesh gradient + glass card ── */
const LeftPanel = styled.div`
  position: relative;
  flex: 0 0 50%;
  width: 50%;
  min-width: 0;
  height: 100%;
  min-height: 100%;
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
  max-width: 31rem;
  margin: 0 clamp(0.75rem, 3vw, 2rem);
  padding: clamp(1.5rem, 2.5vw, 2.75rem);
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
  font-size: clamp(2.1rem, 3.6vw, 3.5rem);
  font-weight: 800;
  line-height: 1.1;
  letter-spacing: -0.025em;
  color: ${COLORS.white};
  margin: 0 0 1.5rem;

  @media (max-width: 1366px) {
    font-size: 3rem;
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


/* ── RIGHT PANEL: Login form ── */
const RightPanel = styled.div`
  flex: 1 1 50%;
  width: 50%;
  min-width: 0;
  height: 100%;
  min-height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: clamp(0.5rem, 1.5vh, 1rem) clamp(0.9rem, 2.2vw, 2.2rem);
  background: linear-gradient(135deg, #f0f4f8 0%, #e2e8f0 100%);
  position: relative;
  overflow-y: auto;
  overflow-x: hidden;

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
`;

const GlassFormContainer = styled.div`
  position: relative;
  z-index: 10;
  width: 100%;
  max-width: 30rem;
  max-height: calc(100dvh - 2rem);
  overflow-y: auto;
  padding: clamp(0.85rem, 1.5vw, 1.4rem) clamp(1rem, 2vw, 1.85rem);
  background: rgba(255, 255, 255, 0.7);
  backdrop-filter: blur(20px);
  border: 1px solid rgba(255, 255, 255, 0.8);
  border-radius: 1.75rem;
  box-shadow: 0 8px 32px 0 rgba(10, 37, 64, 0.08);

  @media (max-width: 640px) {
    padding: 1.25rem 1.5rem;
  }
`;

const FormHeading = styled.h1`
  font-size: 1.75rem;
  font-weight: 800;
  letter-spacing: -0.025em;
  color: ${COLORS.brandBlue};
  margin: 0 0 0.35rem;
  line-height: 1.2;
  text-align: center;

  @media (min-width: 1024px) {
    text-align: left;
  }

  @media (min-width: 1280px) {
    font-size: 1.875rem;
  }
`;

const FormSubheading = styled.p`
  font-size: 0.9375rem;
  font-weight: 500;
  color: ${COLORS.slate600};
  margin: 0 0 0.875rem;
  line-height: 1.4;
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

  /* ── Base styles shared by both username (.ant-input-affix-wrapper)
         and password (.ant-input-password.ant-input-affix-wrapper) ── */
  .ant-input-affix-wrapper,
  .ant-input {
    border-radius: 1.125rem !important;
    border: 1px solid rgba(255, 255, 255, 0.4) !important;
    background: rgba(255, 255, 255, 0.5) !important;
    backdrop-filter: blur(4px);
    padding: 0.9rem 3rem 0.9rem 3rem !important;
    font-size: 1rem !important;
    color: ${COLORS.brandBlue} !important;
    /* Suppress Ant Design's default blue focus ring so both fields look identical */
    box-shadow: none !important;
    outline: none !important;
    transition: border-color 0.2s ease, background 0.2s ease !important;

    &:hover {
      border-color: rgba(255, 255, 255, 0.7) !important;
      background: rgba(255, 255, 255, 0.6) !important;
    }

    &:focus,
    &.ant-input-affix-wrapper-focused {
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

  /* ── Inner <input> inside any affix-wrapper (both username and password) ── */
  .ant-input-affix-wrapper > input.ant-input {
    padding: 0 !important;
    background: transparent !important;
    border: none !important;
    box-shadow: none !important;
    outline: none !important;

    &:focus {
      border: none !important;
      box-shadow: none !important;
      outline: none !important;
    }

    &::selection {
      background: rgba(10, 37, 64, 0.15);
      color: ${COLORS.brandBlue};
    }
  }

  /* ── Autofill override (username field — bare <input class="ant-input">) ──
   *
   * The username <Input> renders as a bare <input class="ant-input"> with full
   * padding (0.9rem 1rem 0.9rem 3rem).  The -webkit-box-shadow inset trick
   * fills the entire padded area with white, so the whole box looks filled.
   */
  .ant-input:-webkit-autofill,
  .ant-input:-webkit-autofill:hover,
  .ant-input:-webkit-autofill:focus {
    -webkit-text-fill-color: ${COLORS.brandBlue} !important;
    caret-color: ${COLORS.brandBlue};
    -webkit-box-shadow: 0 0 0 1000px rgba(255, 255, 255, 0.8) inset !important;
    box-shadow: 0 0 0 1000px rgba(255, 255, 255, 0.8) inset !important;
    border-radius: 1.125rem !important;
    transition: background-color 9999s ease-in-out 0s;
  }

  /* ── Autofill override (password field) ──────────────────────────────────
   *
   * <Input.Password> renders differently from <Input>:
   *
   *   <span class="ant-input-affix-wrapper ant-input-password">   ← WRAPPER
   *     <input type="password" style="padding:0">                 ← inner input
   *     <span class="ant-input-suffix">eye-icon</span>
   *   </span>
   *
   * The inner input has padding:0, so applying box-shadow inset to it fills
   * only a tiny zero-height rectangle — visually a "small oval" in the centre
   * of the field.  The wrapper's background never changes.
   *
   * Fix:
   *  1. Use :has(input:-webkit-autofill) on the WRAPPER so the full visible
   *     box area gets the same white background as the username field.
   *  2. Keep the inner input transparent so the wrapper background shows.
   *  3. Hide the browser's credential auto-fill button (:-webkit-credentials-
   *     auto-fill-button) which also appears as a small oval icon overlay.
   */

  /* Step 1 — Fill the entire password wrapper when inner input is autofilled */
  .ant-input-password.ant-input-affix-wrapper:has(input:-webkit-autofill),
  .ant-input-password.ant-input-affix-wrapper:has(input:-webkit-autofill:hover),
  .ant-input-password.ant-input-affix-wrapper:has(input:-webkit-autofill:focus) {
    background: rgba(255, 255, 255, 0.8) !important;
    border-color: rgba(255, 255, 255, 0.7) !important;
    transition: background-color 9999s ease-in-out 0s;
  }

  /* Step 2 — Inner password <input> stays transparent so wrapper bg shows */
  .ant-input-password > input.ant-input,
  .ant-input-password > input.ant-input[type='password'] {
    background: transparent !important;
    border: none !important;
    box-shadow: none !important;
    -webkit-box-shadow: none !important;
  }

  .ant-input-password > input.ant-input[type='password']:-webkit-autofill,
  .ant-input-password > input.ant-input[type='password']:-webkit-autofill:hover,
  .ant-input-password > input.ant-input[type='password']:-webkit-autofill:focus {
    -webkit-text-fill-color: ${COLORS.brandBlue} !important;
    caret-color: ${COLORS.brandBlue};
    -webkit-box-shadow: 0 0 0 1000px transparent inset !important;
    box-shadow: 0 0 0 1000px transparent inset !important;
    background: transparent !important;
    transition: background-color 9999s ease-in-out 0s;
  }

  /* Step 3 — Hide the browser's credential auto-fill button overlay (oval/key
   * icon that Chrome/Edge shows inside password fields for saved credentials).
   * The autofill feature itself continues to work; only the visual badge is
   * suppressed so the field looks identical to the username field. */
  .ant-input-password input[type='password']::-webkit-credentials-auto-fill-button,
  input[type='password']::-webkit-credentials-auto-fill-button {
    visibility: hidden;
    pointer-events: none;
    position: absolute;
    right: 0;
  }

  /* ── Show/hide password eye icon ── */
  .ant-input-password-icon {
    border: none !important;
    background: transparent !important;
    box-shadow: none !important;
    color: ${COLORS.slate400} !important;
  }

  .ant-input-password-icon:hover,
  .ant-input-password-icon:focus,
  .ant-input-password-icon:focus-visible {
    border: none !important;
    background: transparent !important;
    box-shadow: none !important;
    outline: none !important;
    color: ${COLORS.brandBlue} !important;
  }

  /* Suppress MS Edge's built-in password reveal button */
  input[type='password']::-ms-reveal,
  input[type='password']::-ms-clear {
    display: none;
  }

input[type='password']::-webkit-credentials-auto-fill-button,
input[type='password']::-ms-reveal,
input[type='password']::-ms-clear {
  display: none !important;
  visibility: hidden !important;
  pointer-events: none;
}

input[type='password'] {
  appearance: none !important;
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
  width: 100%;
  flex: 1;
  min-width: 0;
  height: 2.5rem !important;
  border-radius: 0.5rem !important;
  border: none !important;
  background: rgba(255, 255, 255, 0.6) !important;
  box-shadow: none !important;
  outline: none !important;
  font-size: 0.875rem !important;
  font-weight: 600 !important;
  letter-spacing: 0.1em !important;
  text-transform: uppercase !important;
  color: ${COLORS.brandBlue} !important;

  &:focus {
    border: none !important;
    box-shadow: none !important;
    outline: none !important;
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
  font-size: 1.3rem;
  font-weight: 700;
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

// const CaptchaIndicator = styled.div`
//   flex-shrink: 0;
//   color: ${COLORS.slate400};
// `;

const LoginButton = styled(Button)`
  width: 100%;
  height: 2.75rem;
  border-radius: 0.875rem;
  font-size: 1.125rem;
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

const SsoDivider = styled.div`
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.75rem;
  margin: 0.65rem 0;
  width: 100%;
`;

const SsoDividerLine = styled.div`
  flex: 1;
  height: 1px;
  background: ${COLORS.slate300};
`;

const SsoDividerText = styled.span`
  font-size: 0.75rem;
  font-weight: 700;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  color: ${COLORS.slate500};
`;

const SsoButton = styled(Button)`
  width: 100%;
  height: 2.75rem;
  border-radius: 0.875rem;
  font-size: 0.9375rem;
  font-weight: 700;
  border: 1px solid ${COLORS.brandBlue} !important;
  color: ${COLORS.brandBlue} !important;
  background: rgba(255, 255, 255, 0.85) !important;

  &:hover {
    color: ${COLORS.brandBlueDark} !important;
    border-color: ${COLORS.brandBlueDark} !important;
    background: rgba(255, 255, 255, 1) !important;
  }
`;

const EnterpriseDivider = styled.div`
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
  margin-top: 1rem;
  margin-bottom: 0.5rem;
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
  gap: 1.25rem;
  color: ${COLORS.slate500};
  margin-bottom: 0.5rem;
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

// const ForgotLink = styled.a`
//   font-size: 0.75rem;
//   font-weight: 700;
//   color: ${COLORS.brandBlue};
//   text-decoration: none;

//   &:hover {
//     text-decoration: underline;
//   }
// `;

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
  const [isSsoModalOpen, setIsSsoModalOpen] = useState(false);
  const [captchaCode, setCaptchaCode] = useState<string>(generateCaptcha);
  const [userCaptchaInput, setUserCaptchaInput] = useState<string>('');
  const dispatch = useDispatch();
  const [showPassword, setShowPassword] = useState(false);
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
    const loginAttemptedAt = sessionStorage.getItem('login_attempted_at');

    // Only show the error when the redirect happened within 30 seconds of the
    // login attempt. A failed login redirects back immediately (< a few seconds),
    // whereas a logout redirect can happen hours later. Without this guard the
    // flag left by a previous successful login would trigger a false "invalid
    // credentials" toast every time the user logs out.
    const isRecentAttempt =
      loginAttemptedAt !== null &&
      Date.now() - parseInt(loginAttemptedAt, 10) < 30_000;

    sessionStorage.removeItem('login_attempted');
    sessionStorage.removeItem('login_attempted_at');

    if (loginAttempted === 'true' && isRecentAttempt) {
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
    sessionStorage.setItem('login_attempted_at', Date.now().toString());
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

  const closeSsoModal = () => setIsSsoModalOpen(false);

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
        style={{ marginBottom: 16 }}
      >
        <div>
          <FormLabel>{t('Username')}</FormLabel>
          <InputWrapper>
            <InputIcon>
              <Icons.UserOutlined iconSize="m" />
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
        style={{ marginBottom: 16 }}
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
            <div style={{ position: 'relative' }}>
              <Input
                type={showPassword ? 'text' : 'password'}
                placeholder="••••••••"
                data-test="password-input"
              />

              <span
                style={{
                  position: 'absolute',
                  right: '12px',
                  top: '50%',
                  transform: 'translateY(-50%)',
                  cursor: 'pointer',
                  zIndex: 2,
                  color: '#64748b',
                }}
                onClick={() => setShowPassword(prev => !prev)}
              >
                {showPassword ? (
                  <Icons.EyeInvisibleOutlined iconSize="m" />
                ) : (
                  <Icons.EyeOutlined iconSize="m" />
                )}
              </span>
            </div>
          </InputWrapper>
        </div>
      </Form.Item>

      <Form.Item style={{ marginBottom: 16 }}>
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
        <SsoDivider>
          <SsoDividerLine />
          <SsoDividerText>{t('OR')}</SsoDividerText>
          <SsoDividerLine />
        </SsoDivider>

        <Form.Item style={{ marginBottom: 0 }}>
          <SsoButton
            type="default"
            htmlType="button"
            onClick={() => setIsSsoModalOpen(true)}
            data-test="login-sso-button"
          >
            {t('Login with SSO')}
          </SsoButton>
        </Form.Item>
        <Modal
          show={isSsoModalOpen}
          onHide={closeSsoModal}
          name={t('SSO Login')}
          title={t('SSO Login')}
          maskClosable
          footer={
            <>
              <Button buttonStyle="secondary" onClick={closeSsoModal}>
                {t('Cancel')}
              </Button>
              <Button buttonStyle="primary" onClick={closeSsoModal}>
                {t('OK')}
              </Button>
            </>
          }
        >
          {t('AD not present, please contact to CX InsightsHub admin')}
        </Modal>
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
      </LeftPanel>

      {/* Right panel - login form */}
      <RightPanel>
        <GlassFormContainer>
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
