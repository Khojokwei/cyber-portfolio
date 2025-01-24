# cyber-portfolio
PROJECT 1
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





PROJECT 2
````markdown
# Linux SSH and File Download Project

This project demonstrates how to connect to a remote server using SSH, host a file with an HTTP server, and download the file using the `wget` command. The downloaded file is then read and its contents displayed.

## Objectives
- Use SSH to connect to a remote server.
- Start an HTTP server using Python 3.
- Download a file hosted on the HTTP server using `wget`.
- Display the contents of the downloaded file.

---

## Steps

### 1. **Connect to the Remote Server via SSH**
Use the `ssh` command to connect to the server.  
**Details**:
- **Username**: `tryhackme`
- **IP Address**: `10.10.80.222`
- **Password**: `tryhackme`

**Command**:
```bash
ssh tryhackme@10.10.80.222
````

Enter the password `tryhackme` when prompted.
Run a terminal

---

### 2. **Start an HTTP Server**

On the remote server, use Python 3 to start an HTTP server in the current directory.

**Command**:

```bash
python3 -m http.server
```

- The server will run on the default port `8000` unless specified otherwise.
- Keep this tab open to maintain the HTTP server's operation.

---

### 3. **Open a New Tab for File Download**

To avoid terminating the running HTTP server, open a new terminal tab. In the new tab, use the `wget` command to download the file hosted on the HTTP server.

**Details**:

- **File Name**: `.flag.txt`
- **URL**: `http://10.10.80.222:8000/.flag.txt`

**Command**:

```bash
wget http://10.10.80.222:8000/.flag.txt
```

---

### 4. **Verify the File Download**

After downloading the file, verify its presence in the local directory by listing all files, including hidden ones.

**Command**:

```bash
ls -a
```

Look for the file named `.flag.txt` in the output.

---

### 5. **Read the Contents of the File**

Use the `cat` command to display the contents of the downloaded file.

**Command**:

```bash
cat .flag.txt
```

**Output**:

```
THM{WGET_WEBSERVER}
```

---

## Key Notes

1. **Why Open a New Tab?**

   - Opening a new terminal tab ensures the HTTP server continues running in the original tab, allowing the file to remain accessible for download.

2. **Security Considerations**:

   - Ensure the SSH credentials and server IP are secured and not publicly exposed.
   - Clean up sensitive files like `.flag.txt` after use.

---

## Output Summary

By following the steps above, the following result is achieved:

- File `.flag.txt` is successfully downloaded to the local directory.
- The contents of the file are displayed as:
  ```
  THM{WGET_WEBSERVER}
  ```

---

## Technologies Used

- **Linux Terminal**
- **SSH** for secure remote connection.
- **Python 3** for hosting an HTTP server.
- **wget** for file download.

---



