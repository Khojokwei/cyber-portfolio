# cyber-portfolio
# Identifying and Blocking a Malicious IP Address

## Objective  
To identify a potentially malicious IP address and take the necessary steps to block it using a SIEM dashboard and firewall configuration.

---

## Steps Taken

1. **Identifying the Unknown IP**  
   - Located the suspicious IP address `143.110.250.149` on the SIEM dashboard.

2. **Verifying the IP's Authenticity**  
   - Used [ipinfo.io](https://ipinfo.io) to analyze the IP address.  
   - Confirmed that the IP was malicious, originating from a Chinese company.

3. **Taking Action**  
   - Reported the findings to the SOC Lead.  
   - Gained authorization to configure the firewall.

4. **Blocking the Malicious IP**  
   - Entered the IP address into the firewall's block list.  
   - Successfully blocked the IP, with confirmation displayed as `TH{THREAT-BLOCKED}`.

---

## Outcome  
The malicious IP was successfully identified and blocked, ensuring enhanced network security.
