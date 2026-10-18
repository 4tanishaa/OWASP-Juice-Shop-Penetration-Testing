# OWASP Juice Shop — Black-Box Penetration Testing

## Project Overview
This project documents manual security testing of a locally running OWASP Juice Shop web application using Burp Suite Community Edition.

## Objective
To examine web application behavior, test security controls, capture HTTP request and response evidence, and document verified findings.

## Tools Used
- OWASP Juice Shop
- Docker Desktop
- Burp Suite Community Edition
- Google Chrome

## Testing Performed
- Reviewed application HTTP traffic using Burp Suite.
- Tested login behavior with valid and invalid credentials.
- Examined the application configuration endpoint.
- Tested the current-user endpoint with and without authentication.

## Evidence
Screenshots of selected test requests and responses are available in the `Evidence` folder.

## Results and Limitations
The invalid-login test returned `401 Unauthorized`, as expected. The configuration endpoint returned `200 OK`, but no sensitive information was confirmed in the response. The current-user endpoint returned an empty user object when authentication was removed.

These observations are not presented as confirmed vulnerabilities. Further testing is required before assigning vulnerability severity or CVSS scores.

## Scope
Testing was performed against a local OWASP Juice Shop instance for educational purposes.

## Disclaimer
This project is intended for authorized educational security testing only.
