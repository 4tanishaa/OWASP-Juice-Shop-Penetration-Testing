# Finding 03: Basket Access-Control Test

**Application:** OWASP Juice Shop — local test instance  
**Endpoint:** Basket API request captured in Burp Suite  
**Test category:** Authentication and access control  
**Status:** No vulnerability confirmed

## Objective
Determine whether the basket endpoint rejects requests made without authentication.

## Test Procedure
1. Captured a basket-related request using Burp Suite.
2. Sent the request with the existing authenticated session.
3. Removed the authorization header and session cookie.
4. Resent the request without authentication.

## Observed Results
- Authenticated request: `304 Not Modified`.
- Request without authentication: `401 Unauthorized`.

The authenticated response was affected by caching and did not provide a conclusive functional result. The unauthenticated request was rejected.

## Conclusion
No unauthorized basket-data access was demonstrated during this test. The result does not establish a vulnerability.

## Recommendation
Retain authentication and authorization checks on private basket operations. For further validation, repeat the authenticated request without conditional cache headers and compare the response.

## Evidence
Attach a redacted Burp request/response screenshot if available. Remove cookies, tokens, and personal information before publication.
