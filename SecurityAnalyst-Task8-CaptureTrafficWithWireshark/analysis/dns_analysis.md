# DNS Traffic Analysis

## Objective

Capture and analyze DNS traffic using Wireshark to understand how a domain name is resolved into an IP address.

## Tool Used

- Wireshark
- Kali Linux
- Firefox Browser

## Display Filter

  - dns

## Test Performed

I generated DNS traffic by opening **facebook.com** in the browser while Wireshark was capturing network traffic.

## Observations

The Wireshark capture showed the DNS resolution process for **facebook.com**.

- A **Standard DNS Query** was sent from the client requesting the IP address of `facebook.com`.
- The DNS server returned a **Standard DNS Response** containing the corresponding IP address records.
- This process allowed the browser to locate the destination server before establishing an HTTP/HTTPS connection.

## Packet Details

| Field | Value |
|--------|--------|
| Protocol | DNS |
| Domain Queried | facebook.com |
| Query Type | Standard Query |
| Response | Standard Query Response |

> Replace the packet number or IP address with the exact values from your Wireshark capture if needed.

## Security Analysis

- Traditional DNS queries are usually unencrypted.
- Attackers monitoring network traffic may identify which domains users are accessing.
- Secure DNS technologies such as **DNS over HTTPS (DoH)** and **DNS over TLS (DoT)** help protect DNS queries from interception.

## Evidence

Screenshot: `05_dns_filter.png`

## Conclusion

The capture successfully demonstrated how a DNS client requests the IP address for **facebook.com** and how the DNS server responds, making DNS an essential service for network communication.