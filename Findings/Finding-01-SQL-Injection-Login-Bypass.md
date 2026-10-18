# Finding 01: Potential SQL Injection in Login

**Application:** OWASP Juice Shop (local test instance)  
**Endpoint:** `POST /rest/user/login`  
**Category:** Injection / Authentication Bypass  
**Severity:** High — provisional, pending impact assessment  
**CVSS v3.1:** Pending validation

## Description
During authorized black-box testing, a SQL injection-style payload was submitted in the login email field. The request returned `200 OK`, and the tester reported successful login despite supplying an incorrect password.

The request and response must be retained as evidence, with authentication tokens and account details redacted.

## Steps to Reproduce
1. Open the local Juice Shop instance.
2. Intercept the login request using Burp Suite.
3. Submit the test payload `' OR true--` in the email field and a deliberately incorrect test password.
4. Send the request and inspect the HTTP response.
5. Verify whether the application establishes an authenticated session despite the incorrect password.

## Observed Result
The tester reported a `200 OK` response and successful login. Confirm that the saved request contains the exact payload and incorrect password before treating the bypass as confirmed.

## Expected Result
Invalid credentials and untrusted input should never bypass authentication.

## Potential Impact
If confirmed, an attacker may be able to bypass login and access functionality or data available to an authenticated user. The actual impact depends on the privileges and data accessible through the resulting session.

## Remediation
- Use parameterized SQL queries or prepared statements.
- Avoid building SQL queries by concatenating user-supplied input.
- Apply server-side input handling and safe database access patterns.
- Add automated tests for invalid credentials and injection payloads.

## Evidence
Attach a Burp Suite request/response screenshot in the project's `Evidence` folder. Redact tokens, passwords, cookies, email addresses, and other sensitive values.

## Validation Status
Pending final review of the exact request, response, and authenticated session behavior.
