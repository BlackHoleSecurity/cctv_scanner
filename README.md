## CCTV NMap Scanner & Vulnerability Tester

**Author**: ITermSec  
**Team**: BlackHole Security  
**Version**: 1.0  

This tool is a network scanner optimized for discovering open CCTV / IP cameras on your own network, equipped with vulnerability testing features such as authentication bypass, SQL injection, and Remote Code Execution (RCE) on common CCTV devices (Hikvision, Dahua, etc.).

## Warning

This tool is intended for use **only on your own network** or devices for which you have explicit written permission. Unauthorized access to devices you do not own is illegal in many jurisdictions. The author and team are not responsible for any misuse.

## Features

- Scan common CCTV ports (80, 81, 443, 554, 8000, 8080, 34567, etc.) using Nmap
- Detect web interfaces and identify vendor (Hikvision/Dahua)
- Test authentication bypass (default credentials, SQL injection login, path traversal)
- Test SQL injection (error-based, time-based, boolean, union)
- Test RCE / command injection (Linux & Windows payloads)
- Detect specific CVEs such as CVE-2017-7923 (Hikvision), ONVIF default credentials, etc.
- Save scan results to `results.txt`

## Requirements

- Python 3.6+
- Nmap installed on the system
- Python libraries: `python-nmap`, `requests`, `ipaddress`

## Installation
1. Clone the repository (or copy the script to a directory).
```bash
   git clone https://github.com/BlackHoleSecurity/cctv_scanner.git
   cd cctv_scanner
```

2. Install dependencies

```bash
   pip install -r requirements.txt
```

4. Ensure Nmap is installed
   · Linux: sudo apt install nmap
   · Windows: download from nmap.org
   · macOS: brew install nmap

Usage

Run the script with Python:

```bash
python3 scanner.py
```

Follow the on-screen instructions:

1. Enter the target in one of the following formats:
   · 192.168.1.1 (single IP)
   · 192.168.1.1/24 (CIDR subnet)
   · 192.168.1.1-255 (IP range)
2. After the port scan finishes, you will be asked:
   ```
   Do you want to test for vulnerabilities? (y/n)
   ```
   Choose y to test authentication bypass, SQL injection, and RCE.

Example

```bash
Enter Target : 192.168.1.1/24
```

The scan output will show:

· Open ports
· Web page titles
· Whether a web interface is detected (with vendor if identifiable)
· If vulnerability testing is enabled: bypass results, SQLi, RCE, and known CVEs.

Results are saved to results.txt.

Sample Output

```
[+] Host        : 192.168.1.100
    Port        : 80 OPEN -> http
      └─ Title  : Hikvision Camera
     [!] Testing authentication bypass (enhanced payloads)...
      [✓] Auth Bypass Found! -> http://192.168.1.100:80/login
      └─ Credentials: admin:12345
```

Disclaimer

This tool is provided for educational purposes and security testing only on your own infrastructure. Unauthorized use violates computer crime laws in many countries. You are solely responsible for your actions.

License

MIT License – feel free to modify and redistribute with credit to the original author.

Contributing

If you want to add new payloads or detect additional CVEs, please open an issue or submit a pull request.

---

Created with care by BlackHole Security

