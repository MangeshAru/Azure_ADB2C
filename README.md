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



---------------------#--------------------#---------------------#----------------------#---------------------------------#---------------

1. Azure Active Directory B2C offers two methods to define how users interact with your applications: through predefined user flows or through fully configurable custom policies.
2. User Flows configuration is GUI-based and they are designed for the most common authentication scenarios. Custom Policies are configured via XML files and are much more complex, but can support a wider range of scenarios.

XML:
-----------------------
ContentDefinitions → describe which page and UI contract to display (sign-in, sign-up, password reset, error, etc.).
ClaimsProviders → bundle one or more technical profiles that do the work (read/write directory, validate credentials, call REST APIs, issue tokens).
UserJourneys → orchestrate a sequence of steps that the user goes through (collect input, validate, read/write, issue token).



**ClaimsSchema**
Purpose: Defines all the claims (pieces of data) that can exist in your policy. Think of it as the “variables” your policy can use.
Key elements:

ClaimType Id: Unique identifier for the claim (e.g., email, objectId, displayName).
DataType: Type of data (string, boolean, int, dateTime, stringCollection).
UserInputType: How it appears on the UI (TextBox, Password, RadioButton).
Restriction: Optional regex or validation rules.

Why important?
Every claim you collect, validate, or return in tokens must be declared here.
ClaimsSchema ensures consistency across UI, validation, and token issuance.

**ClaimsTransformations**
Purpose: Apply logic or operations on claims—like validation, formatting, or creating new claims from existing ones.
Common transformation methods:

AssertBooleanClaimIsEqualToValue: Validate a boolean claim.
FormatStringClaim: Format a string (e.g., append domain to username).
AddItemToStringCollection: Add an item to a collection claim.
AssertDateTimeIsGreaterThan: Compare two date/time claims (used for refresh token revocation).

Why important?
They enforce business rules (e.g., account must be enabled).
They prepare claims for token issuance or directory write.
They enable advanced logic without custom code.
