Task 5: Network Traffic Capture & Analysis using Wireshark

##  Objective
The goal of this task is to:
1. Capture live network traffic using **Wireshark**.
2. Generate different types of network packets by performing various activities.
3. Analyze the captured traffic and identify multiple protocols.
4. Document findings with screenshots and explanations.

This task demonstrates practical skills in packet capture, protocol analysis, and network troubleshooting — all critical for cybersecurity professionals.

---

##  Tools & Utilities Used

### Primary Tool
- **Wireshark** → Open-source network protocol analyzer that captures and inspects packets in real time.

### Supporting Utilities
- **ping** → Generates ICMP traffic to test network connectivity.
- **nslookup** & **dig** → Generate DNS queries.
- **wget** → Generates HTTP/TCP traffic by downloading files.
- **Firefox Browser** → Generates HTTP and HTTPS traffic.
- **Terminal (Kali Linux)** → Command-line traffic generation and testing.

---

##  Step-by-Step Procedure

### 1️⃣ Selecting the Capture Interface
- Launched Wireshark and selected the **active network interface** (`wlan0` in my case).
- Verified active IP using:
  ```bash
  ip addr

    Started packet capture.

2️⃣ Generating Diverse Network Traffic

To ensure a rich capture for analysis, I performed the following actions:
A. Web Browsing (HTTP & HTTPS)

    Accessed http://example.com (HTTP - unencrypted traffic).

    Accessed https://wikipedia.org (HTTPS - encrypted TLS traffic).

B. DNS Queries

Executed commands:

nslookup openai.com
dig google.com

    These resolved domain names to IP addresses using UDP/TCP port 53.

C. ICMP (Ping)

Executed:

ping -c 4 8.8.8.8

    Generated request/reply packets to Google's DNS server.

D. File Download (HTTP over TCP)

Executed:

wget http://speedtest.tele2.net/1MB.zip

    Generated TCP streams for downloading.

3️⃣ Stopping & Saving the Capture

    Let capture run for ~2 minutes.

    Clicked Stop in Wireshark.

    Saved as:

network_capture.pcapng

 Protocol Analysis & Findings

The following protocols were identified and analyzed:
Protocol	Layer	Transport Layer	Port(s) Used	Description	Screenshot
HTTP	Application	TCP	80	Unencrypted web requests/responses.	screenshot_http.png
HTTPS (TLS)	Application	TCP	443	Encrypted web traffic; TLS handshake visible.	screenshot_https.png
DNS	Application	UDP/TCP	53	Resolves domain names to IPs.	screenshot_dns.png
ICMP	Network	N/A	N/A	Network diagnostics (ping).	screenshot_icmp.png
TCP	Transport	TCP	Various	Reliable transport layer protocol with handshakes.	screenshot_tcp.png
 Screenshots Collected
1. HTTP Traffic

    Shows GET request to example.com over port 80.

    Visible request headers (Host, User-Agent, Accept).

2. HTTPS/TLS Traffic

    Shows TLS handshake (Client Hello, Server Hello).

    All application data encrypted.

3. DNS Queries

    Query: openai.com

    Answer: Resolved to public IP addresses.

4. ICMP Ping

    Request & Reply packets to 8.8.8.8.

5. TCP Streams

    Three-way handshake: SYN → SYN-ACK → ACK.

    Data transfer following handshake.

 Detailed Observations

    DNS before HTTP/HTTPS

        Every domain request begins with a DNS query to resolve hostname → IP.

        In this capture, DNS queries used UDP port 53.

    HTTP in Plain Text

        Headers and content visible in HTTP packets.

        This shows why HTTP is insecure.

    HTTPS Encryption

        No payload visible post-handshake.

        TLS handshake negotiation visible (cipher suites, certificates).

    ICMP Utility

        Verified connectivity to external network.

        Round-trip times visible.

    TCP Reliability

        Captured SYN, SYN-ACK, ACK handshake.

        Retransmissions visible when packet loss occurred.

