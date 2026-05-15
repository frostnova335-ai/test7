<Button
                buttonStyle="primary"
                className="observability-btn"
                title="Visit CX Loop"
                style={{
                  borderRadius: '12px',
                  padding: '10px 18px',
                  fontWeight: 600,
                  fontSize: '14px',

                  background:
                    'linear-gradient(135deg, rgb(242, 106, 33) 0%, rgb(255, 140, 66) 100%)',

                  color: '#ffffff',

                  border: 'none',

                  boxShadow: '0 4px 12px rgba(242, 106, 33, 0.25)',

                  display: 'flex',
                  alignItems: 'center',
                  justifyContent: 'center',

                  gap: '10px',

                  minHeight: '42px',

                  transition: 'all 0.25s ease',

                  cursor: 'pointer',
                }}
                onMouseEnter={e => {
                  e.currentTarget.style.transform = 'translateY(-1px)';
                  e.currentTarget.style.boxShadow =
                    '0 6px 18px rgba(242, 106, 33, 0.35)';
                }}
                onMouseLeave={e => {
                  e.currentTarget.style.transform = 'translateY(0px)';
                  e.currentTarget.style.boxShadow =
                    '0 4px 12px rgba(242, 106, 33, 0.25)';
                }}
                onClick={() =>
                  window.open(
                    'https://cxloop-dev.exlservice.com/cxloop/',
                    '_blank',
                  )
                }
              >
                <img
                  src="/static/images/observability.png"
                  alt="IVA"
                  style={{
                    width: '16px',
                    height: '16px',
                    objectFit: 'contain',
                    filter: 'brightness(0) invert(1)',
                  }}
                />

                <span
                  style={{
                    display: 'flex',
                    alignItems: 'center',
                    lineHeight: 1,
                    marginTop: '1px',
                  }}
                >
                  IVA Observability
                </span>
              </Button>
