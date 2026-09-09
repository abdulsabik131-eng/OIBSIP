Task 1 — Basic Network Scanning with Nmap


Objective
Perform a basic network scan against a local machine/VM using Nmap, identify open ports and running services, perform service-version and OS-detection scans, and document the security relevance of the findings.
> **Ethical scope:** Scan only a machine/VM that you own or have explicit permission to scan. For this task, use a local lab VM such as Kali Linux, Ubuntu, or another intentionally created test machine.
---
1. Install Nmap
Kali Linux / Debian / Ubuntu
```bash
sudo apt update
sudo apt install nmap -y
```
Verify installation
```bash
nmap --version
```
---
2. Identify the Target IP
On the target local VM, run:
```bash
ip addr
```
Look for an IPv4 address such as:
```text
192.168.x.x
```
Set that address as your target.
Example:
```bash
TARGET=192.168.56.101
```
Replace the example IP with the IP of your own lab VM.
---
3. Basic Nmap Scan
Run:
```bash
nmap $TARGET
```
Or directly:
```bash
nmap 192.168.56.101
```
This checks common TCP ports and reports which ports are open.
Save the result:
```bash
nmap $TARGET -oN nmap_scan_results.txt
```
---
4. Service Version Detection
Run:
```bash
nmap -sV $TARGET
```
Save the result:
```bash
nmap -sV $TARGET -oN nmap_service_scan.txt
```
`-sV` attempts to identify the service and version running on discovered open ports.
---
5. OS Detection
Run:
```bash
sudo nmap -O $TARGET
```
Save the result:
```bash
sudo nmap -O $TARGET -oN nmap_os_scan.txt
```
`-O` attempts to identify the target operating system from network characteristics.
If OS detection does not return a result, that can happen because of the VM's network configuration, firewall, or insufficient fingerprinting information.
---
6. Optional: One Combined Scan
For a more complete result in the lab, you can run:
```bash
sudo nmap -sV -O $TARGET -oN nmap_full_results.txt
```
Use the output from this command when preparing the final analysis.
---
7. Record Open Ports and Services
Copy the actual open ports found in your scan into this table.
Port	Protocol	Service	Version	Security Analysis
XX	TCP	Example service	Example version	Explain whether exposure is expected and any risk
XX	TCP	Example service	Example version	Explain whether exposure is expected and any risk
Example analysis
Do not copy this example as your actual finding:
> Port 22/TCP is commonly used by SSH. If SSH is intentionally exposed in the lab, it may be expected. In a real environment, SSH should be restricted to authorized users/networks, use strong authentication, and be kept patched.
Write the analysis based on the actual service/version discovered on your own VM.
---
8. Screenshots
Add screenshots to the GitHub repository showing:
Nmap installation/version:
```bash
   nmap --version
   ```
Basic scan:
```bash
   nmap $TARGET
   ```
Service version scan:
```bash
   nmap -sV $TARGET
   ```
OS detection:
```bash
   sudo nmap -O $TARGET
   ```
Suggested folder:
```text
screenshots/
├── nmap_version.png
├── basic_scan.png
├── service_scan.png
└── os_detection.png
```
---
9. What is Nmap?
Nmap (Network Mapper) is a network discovery and security auditing tool. It can identify reachable hosts, open ports, services, service versions, and, when possible, operating-system characteristics.
10. Why Network Scanning Matters
Network scanning helps security teams understand the attack surface of a system. Open ports can reveal services that are intentionally or unintentionally exposed. Identifying those services and their versions helps defenders verify whether the exposure is expected and whether additional hardening or patching may be required.
11. Ethical Considerations
Nmap can be used for legitimate security testing, but scanning systems without authorization may be inappropriate or illegal.
For this task:
Use only your own local VM/lab.
Do not scan public IP addresses or production systems.
Do not perform scans against college/company infrastructure unless explicitly authorized.
Keep the target and results limited to the assigned lab environment.
---
12. Suggested Repository Structure
```text
nmap-basic-scan/
├── README.md
├── nmap_scan_results.txt
├── nmap_service_scan.txt
├── nmap_os_scan.txt
└── screenshots/
    ├── nmap_version.png
    ├── basic_scan.png
    ├── service_scan.png
    └── os_detection.png
```
---
13. Final Checklist
[ ] Nmap installed
[ ] Nmap version documented
[ ] Local VM target identified
[ ] Basic scan completed
[ ] Service-version scan completed
[ ] OS detection attempted
[ ] Open ports listed
[ ] Service on each open port explained
[ ] Security risk/relevance discussed
[ ] Scan results saved as `.txt`
[ ] Screenshots added
[ ] README completed
[ ] GitHub repository updated
Commands Used
```bash
sudo apt update
sudo apt install nmap -y
nmap --version
ip addr
TARGET=<YOUR_LOCAL_VM_IP>
nmap $TARGET
nmap $TARGET -oN nmap_scan_results.txt
nmap -sV $TARGET
nmap -sV $TARGET -oN nmap_service_scan.txt
sudo nmap -O $TARGET
sudo nmap -O $TARGET -oN nmap_os_scan.txt
sudo nmap -sV -O $TARGET -oN nmap_full_results.txt
```
