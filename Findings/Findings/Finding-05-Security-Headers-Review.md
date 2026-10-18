# Finding 05: HTTP Security Headers Review

**Application:** OWASP Juice Shop — local test instance  
**Endpoint:** `GET /`  
**Test category:** Security configuration  
**Status:** Hardening observation — impact not established  
**Severity:** Informational / undetermined  
**CVSS v3.1:** Not assigned

## Objective
Review the application's HTTP response for common browser security headers.

## Test Procedure
1. Captured the home-page request in Burp Suite.
2. Sent the request to Repeater.
3. Inspected the response headers for Content-Security-Policy, Strict-Transport-Security, X-Content-Type-Options, and X-Frame-Options.

## Observed Results
- `X-Content-Type-Options`: Present
- `X-Frame-Options`: Present
- `Content-Security-Policy`: Not observed in the inspected response
- `Strict-Transport-Security`: Not observed in the inspected response

## Assessment
A missing Content Security Policy may reduce defense-in-depth against some client-side injection attacks. However, this test alone does not demonstrate an exploitable vulnerability. HSTS is generally applicable to HTTPS deployments and should be assessed in the context of the actual deployment.

## Recommendations
- Evaluate and deploy an appropriate Content Security Policy.
- Configure HSTS for production HTTPS deployments, where appropriate.
- Continue using `X-Content-Type-Options: nosniff` and a suitable anti-framing policy.
- Retest after configuration changes.

## Evidence
Attach a screenshot of the response headers from Burp Suite. Redact cookies, tokens, and other sensitive information.

## Limitations
This was a local HTTP test. Production behavior may differ, and the absence of a header in one response does not prove that it is absent throughout the application.
