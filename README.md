# Azure_ADB2C
Understanding Azure AD B2C

What is Azure AD B2C?

Customer Identity Management (CIAM): A turnkey solution to authenticate millions of users and billions of sign-ins daily for consumer-facing apps.
Multiple identity providers: Supports social logins (Google, Facebook, Microsoft), OpenID Connect, SAML, and local accounts (username/password).
Highly customizable UI: Full branding control—custom HTML, CSS, JavaScript—to match the look and feel of your apps.

Why use Azure AD B2C?

Scalable & secure: Handles high authentication loads, protects against DDoS and brute-force attacks, and includes built-in monitoring.
Simplified user experience: Easy to add self-service sign-up, password reset, and profile management without building from scratch.
Cost-effective: Pay-as-you-go pricing model—only pay for active users.
SSO across apps: Enables single sign-on for your web, mobile, and API apps using industry-standard protocols.
Regulatory compliance: Built-in MFA, conditional access, and support for data residency and privacy requirements.

How Azure AD B2C is used

Create a B2C tenant in the Azure portal.
Configure identity providers:

Social accounts (e.g., Facebook, Google).
Local accounts with email/password.


Use built-in user flows or custom policies:

User flows for standard scenarios (sign-up/sign-in, password reset).
Custom policies (XML-based) allow full control over UI, logic, and token content. [learn.microsoft.com], [github.com]


Register applications:

Front-end apps request tokens via OpenID Connect/OAuth2 endpoints.
API apps validate these tokens to authorize requests.


Implement user journeys:

B2C orchestrates steps like credentials collection, validation, directory writes, token issuance, logout handling.
Tokens include claims your app can rely on (e.g., email, name).
A typical journey: user clicks “sign in,” B2C shows a login screen, authenticates, then issues a token back to your app.
