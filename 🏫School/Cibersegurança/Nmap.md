### 1. **Host Discovery**

```bash
nmap -sn <target>
```

- Disables port scanning.
- Performs host discovery to identify live hosts.
### 2. **Port Scanning**

```bash
nmap -p <port_range> <target>
```

- Scans specified ports or port ranges on the target.
### 3. **Service Version Detection**

```bash
nmap -sV <target>
```

- Detects versions of services running on open ports.
### 4. **Operating System Detection**

```bash
nmap -O <target>
```

- Identifies the operating system of the target host.
### 5. **Aggressive Scan**

```bash
nmap -A <target>
```

- Performs:
    - OS detection
    - Version detection
    - Script scanning
    - Traceroute
### 6. **UDP Scan**

```bash
nmap -sU -p <port_range> <target>
```

- Scans specified UDP ports on the target.
### 7. **TCP Connect Scan**

```bash
nmap -sT <target>
```

- Performs a full TCP connect scan.
- Determines if ports are open or closed.
### 8. **SYN Scan (Stealth Scan)**

```bash
nmap -sS <target>
```

- Stealth scan that identifies open ports **without completing** the TCP handshake.
### 9. **Firewall Evasion**

```bash
nmap -T<0-5> <target>
```

- Adjusts timing templates to evade:
    - Firewalls
    - Intrusion Detection Systems (IDS)
### 10. **Scan from File**

```bash
nmap -iL <input_file> <target>
```

- Reads target hosts from a file and performs the scan.
### 11. **Scan All Ports**

```bash
nmap -p- <target>
```

- Scans **all 65,535** ports on the target.
### 12. **Service Enumeration**

```bash
nmap --script <script_name> <target>
```

- Uses Nmap Scripting Engine (NSE) to:
    - Enumerate services
    - Gather additional info
### 13. **Scan Specific Ports**

```bash
nmap -p <port1>,<port2>,<port3> <target>
```

- Scans specific ports on the target.