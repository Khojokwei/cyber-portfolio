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

PROJECT 3
# FTP File Download Project - Retrieve Hidden Flag

## Overview
This project demonstrates how to use **File Transfer Protocol (FTP)** to connect to a remote server, navigate through directories, download a file, and reveal hidden contents. The task involved downloading a file named `flag.txt` from a server with the IP address `10.10.62.72`, and the hidden content in that file was a flag that I had to find.

## Steps Involved

### 1. **Connecting to the FTP Server**
I started by connecting to the FTP server at `10.10.62.72` using the following command in my terminal:
ftp 10.10.62.72
This initiated a connection to the FTP server. Once the connection was established, the system prompted me for the **username**.

### 2. **Logging in Using Anonymous Access**
Upon connection, the FTP client prompted me for a **username** and **password**. Since this server allows **anonymous access**, I entered `anonymous` as the username. The password field was left blank, and I pressed **Enter** to proceed.
Username: anonymous
Password: (pressed Enter for no password)
The server then returned a **login successful** message, confirming that I had logged in successfully without needing any specific credentials.

### 3. **Listing Files and Directories**
After logging in, I typed the `ls` command to list the files and directories on the server:
ls
This displayed several files, including `tea.txt`, `file.txt`, and `flag.txt`. The file I was looking for was `flag.txt`, which contained the hidden flag.

### 4. **Switching to ASCII Mode**
To ensure the contents of the text file would be displayed correctly, I typed the command:
type ascii
This switched the FTP client to **ASCII mode** for proper text file handling. FTP can transfer files in two modes: **binary** (for non-text files) and **ASCII** (for text files).

### 5. **Downloading the File**
Once in ASCII mode, I downloaded the file using the `get` command:
get flag.txt
The FTP client displayed several messages, and the last message was:
Transfer complete
This confirmed that the file was successfully downloaded to my local machine.

### 6. **Quitting the FTP Session**
To exit the FTP session, I typed:
quit
This returned me to my home directory on the local machine.

### 7. **Viewing the File Contents**
To verify the contents of the downloaded `flag.txt` file, I listed the files in my home directory using the `ls` command:
ls
I saw that `flag.txt` was listed among the files. I then displayed the contents of the file using the `cat` command:
cat flag.txt
The message displayed in the file was:
THM{FAST-FTP}

### 8. **Conclusion**
The project was successful! I was able to use FTP to connect to the remote server, download a file, and retrieve the hidden flag. This project demonstrates how **network protocols** like FTP can be used to interact with remote servers and manage files.

## Technologies Used:
- **FTP (File Transfer Protocol)**
- **Linux Command Line** (for FTP and file handling)
- **Bash/Shell commands** (for displaying the file's contents)


## Conclusion
This project demonstrates how FTP can be used to download files from a server, as well as how to manipulate and display hidden file contents using Linux commands. The skills learned in this project are valuable for anyone working with remote servers or in a cybersecurity context.

PROJECT 4
#!/bin/bash

################################################################################
# PROJECT: Hash Cracking with Hashcat
# PURPOSE: This script automates the process of identifying and cracking a SHA-512
#          Crypt hash ($6$) using Hashcat and the rockyou.txt wordlist.
#
# KEYWORDS: Hashing, Hashcat, Cryptography, SHA-512 Crypt, Password Cracking,
#           Cybersecurity, Dictionary Attack, RockYou Wordlist, Ethical Hacking.
#
# TERMINOLOGIES:
# - Hash: A fixed-length representation of data, used for security (e.g., passwords).
# - Hashcat: A powerful password recovery tool that cracks hashes using different attacks.
# - SHA-512 Crypt: A secure hashing algorithm commonly used for password storage.
# - Dictionary Attack: An attack method where a wordlist (e.g., rockyou.txt) is used to find
#   the correct password by comparing each word against the hash.
# - RockYou.txt: A popular password list used in cybersecurity research and penetration testing.
################################################################################

# Create the directory for storing the hash file
mkdir -p ~/Hashing-Basics/Task-6

# Save the hash into a file
echo "$6$GQXVvW4EuM$ehD6jWiMsfNorxy5SINsgdlxmAEl3.yif0/c3NqzGLa0P.S7KRDYjycw5bnYkF5ZtB8wQy8KnskuWQS3Yr1wQ0" > ~/Hashing-Basics/Task-6/hash3.txt

# Run Hashcat to crack the password using SHA-512 Crypt mode (1800) and the rockyou.txt wordlist
hashcat -m 1800 -a 0 ~/Hashing-Basics/Task-6/hash3.txt /usr/share/wordlists/rockyou.txt --force

# Show the cracked password
hashcat -m 1800 --show ~/Hashing-Basics/Task-6/hash3.txt



