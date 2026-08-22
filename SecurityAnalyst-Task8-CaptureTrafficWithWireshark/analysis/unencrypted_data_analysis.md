# Unencrypted HTTP Packet Analysis

## Objective

Identify an HTTP packet that contains unencrypted sensitive information using Wireshark.

## Tool Used

- Wireshark
- Kali Linux
- DVWA (Damn Vulnerable Web Application)

## Display Filter

```text
-- http
```

## Test Performed

A login request was submitted to DVWA over HTTP while Wireshark was capturing network traffic.

## Observation

The captured HTTP **POST** request transmitted the login form data in plain text.

The packet showed:

- Username : admin
- Password : password

The packet also used the content type:

`application/x-www-form-urlencoded`

This confirms that the credentials were transmitted without encryption.

## Security Risk

Using HTTP for login forms is insecure because anyone with access to the network traffic can read sensitive credentials directly from captured packets.

## Recommendation

- Use HTTPS instead of HTTP.
- Enable TLS encryption for all login pages.
- Redirect HTTP requests to HTTPS.
- Enable HSTS to prevent insecure connections.

## Evidence

- 03_http_filter.png – HTTP traffic captured in Wireshark.
- 07_unencrypted_data.png – Plain-text credentials visible in the HTTP POST request.

## Conclusion

The analysis successfully demonstrated that HTTP transmits login credentials in plain text, highlighting the importance of HTTPS for protecting sensitive user information.