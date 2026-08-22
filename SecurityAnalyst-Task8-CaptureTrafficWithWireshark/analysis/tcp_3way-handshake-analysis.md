# TCP 3-Way Handshake Analysis

## Objective

Capture and analyze the TCP three-way handshake using Wireshark.

## Display Filter

-- tcp

## Observation

A TCP connection was established between the client and the server using the standard three-way handshake.

| Step | Packet |
|------|--------|
| 1 | SYN |
| 2 | SYN, ACK |
| 3 | ACK |

### Packet Details

- Client IP: 192.168.20.8
- Server IP: 72.153.5.134
- Client Port: 58983
- Server Port: 443 (HTTPS)

## Handshake Explanation

1. The client sent a **SYN** packet to request a new TCP connection.
2. The server replied with **SYN, ACK**, indicating that it accepted the request.
3. The client sent an **ACK** packet, completing the handshake.

After these three packets, the TCP connection was successfully established, allowing secure HTTPS communication.

## Evidence

Screenshot: `06_tcp_handshake.png`