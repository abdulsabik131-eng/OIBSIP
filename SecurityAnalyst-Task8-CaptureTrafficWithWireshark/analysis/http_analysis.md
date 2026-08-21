# HTTP Traffic Analysis

## Filter Used

http

## Observation

The HTTP filter was applied to identify HTTP packets in the
captured traffic.

## Security Observation

- HTTP does not provide encryption. Information transmitted
through HTTP may be visible to someone who can monitor the
network traffic.
- We can see user credentials in plain text (username:password)

## Evidence
- /screenshots/03_http_filter.png
- /screenshots/04_http_captured_creds.png