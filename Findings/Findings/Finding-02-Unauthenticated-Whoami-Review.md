# Finding 02: Unauthenticated Access to User Information — Under Investigation

**Application:** OWASP Juice Shop (local test instance)  
**Endpoint:** `GET /rest/user/whoami`  
**Category:** Authentication / Information Disclosure  
**Severity:** Undetermined  
**CVSS v3.1:** Not assigned — evidence requires further validation

## Description
During local black-box testing, the `/rest/user/whoami` endpoint returned `200 OK` and account-related fields, including email, last login IP, and profile image. The tester reported that these fields remained present after attempting to remove authentication headers and cookies.

This observation requires further validation to establish whether the response genuinely contains account information without authentication or is affected by session state, caching, or another request mechanism.

## Steps to Reproduce
1. Open the local Juice Shop instance.
2. Capture `GET /rest/user/whoami` using Burp Suite.
3. Remove the `Authorization` header and `Cookie` header.
4. Remove conditional cache headers, such as `If-None-Match` and `If-Modified-Since`.
5. Send the request and inspect the response body.
6. Record whether account details are returned without an authenticated session.

## Observed Result
The tester reported `200 OK` and account-related fields. The unauthenticated behavior has not yet been independently confirmed from the raw request and response.

## Expected Result
The endpoint should return only information appropriate to the current authentication state and should not disclose another user's private information.

## Potential Impact
If unauthorized access to private account information is confirmed, the issue may expose personal or session-related data. Actual impact depends on which information is accessible and whether the behavior affects other users.

## Remediation
- Enforce server-side authentication and authorization where required.
- Ensure user information is scoped to the authenticated principal.
- Avoid serving private cached responses to unauthenticated requests.
- Add regression tests for authenticated and unauthenticated requests.

## Evidence
Attach a screenshot of the raw unauthenticated request and response. Redact email addresses, IP addresses, cookies, tokens, and other sensitive values.

## Validation Status
Under investigation. Do not treat this observation as a confirmed vulnerability until authentication state and response behavior are verified.
