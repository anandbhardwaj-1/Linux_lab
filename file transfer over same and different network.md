# 🌐 File Transfer Over Same Network and Different Network Setups

## 1. Introduction

In modern computer networks, *file transfer* is a fundamental operation that allows sharing and synchronization of data between devices.  
Depending on the *network setup*, the approach to transfer files may differ.  
This document explains how to transfer files over:
•⁠  ⁠A *same network (LAN / Wi-Fi)*, and  
•⁠  ⁠A *different network setup (Internet / WAN)*.

---

## 2. Understanding Networks

### 🖧 Local Area Network (LAN)
A *LAN* is a private network connecting devices within a limited area such as a home, office, or campus.  
All devices share a *private IP address range*, such as:

192.168.x.x or 10.x.x.x

File transfers within a LAN are *faster* and *do not require Internet access*.

### 🌍 Wide Area Network (WAN)
A *WAN* connects devices across large geographical areas through the *Internet*.  
Each device has a *public IP address* (assigned by the ISP), allowing remote connections across cities or countries.

---

## 3. Tools Used for File Transfer

| Tool | Description | Works On |
|------|--------------|----------|
| ⁠ scp ⁠ | Secure copy using SSH encryption | Linux / macOS / Windows (via PowerShell or Git Bash) |
| ⁠ sftp ⁠ | Secure FTP over SSH | Cross-platform |
| ⁠ rsync ⁠ | Synchronizes and transfers files efficiently | Linux / macOS |
| ⁠ ftp ⁠ | Basic file transfer protocol (not encrypted) | Legacy systems |
| ⁠ curl ⁠ / ⁠ wget ⁠ | Download or upload files over HTTP/S | Cross-platform |

---

## 4. File Transfer Over the *Same Network*

### 🔹 Scenario
You want to transfer a file between two computers connected to the *same Wi-Fi or LAN*.

### 🧠 Requirements
•⁠  ⁠Both devices must be connected to the same router/network.
•⁠  ⁠The receiving computer must have *SSH enabled*.

### 🧩 Steps

#### Step 1: Find the local IP address of the receiver
On the receiving system, run:
⁠ bash
ip addr show
 ⁠
or
⁠ bash
ifconfig
 ⁠
Example output:

inet 192.168.1.20


#### Step 2: Use SCP to transfer the file
On the sender’s system, run:
⁠ bash
scp /path/to/local/file.txt anand_bhardwaj@192.168.1.20:/home/anand_bhardwaj/
 ⁠

*Explanation:*
•⁠  ⁠⁠ /path/to/local/file.txt ⁠ → the source file path  
•⁠  ⁠⁠ anand_bhardwaj@192.168.1.20 ⁠ → username and receiver's local IP  
•⁠  ⁠⁠ /home/anand_bhardwaj/ ⁠ → destination directory

You’ll be asked for the remote user's password unless key-based login is set up.

#### Step 3: Verify on receiver
On the receiver’s system:
⁠ bash
ls /home/anand_bhardwaj/
 ⁠
You should see the transferred file.

---

## 5. File Transfer Over a *Different Network Setup*

### 🔹 Scenario
You want to transfer a file between two computers *not on the same network* — for example, one in your home and another in your office.

### 🧠 Requirements
•⁠  ⁠The remote machine must have *SSH enabled*.
•⁠  ⁠*Public IP* or *domain name* of the remote machine must be accessible.
•⁠  ⁠Port *22 (SSH)* should be open on the remote machine’s firewall.

### 🧩 Steps

#### Step 1: Find the public IP of the remote system
On the remote system, run:
⁠ bash
curl ifconfig.me
 ⁠
Example output:

203.0.113.25


#### Step 2: Transfer file using SCP
From your local system, run:
⁠ bash
scp file.txt anand_bhardwaj@203.0.113.25:/home/anand_bhardwaj/
 ⁠

If SSH runs on a different port (say 2222):
⁠ bash
scp -P 2222 file.txt anand_bhardwaj@203.0.113.25:/home/anand_bhardwaj/
 ⁠

#### Step 3: Verify transfer remotely
Log in via SSH and check:
⁠ bash
ssh anand_bhardwaj@203.0.113.25
ls -l /home/anand_bhardwaj/
 ⁠

You should see your file safely transferred.

---

## 6. Using SFTP for Interactive Transfers

If you prefer an interactive session, use *SFTP*:

⁠ bash
sftp anand_bhardwaj@203.0.113.25
sftp> put mydata.txt
sftp> get backup.zip
sftp> bye
 ⁠

This method is secure and uses the same encryption as SSH.

---

## 7. Security and Best Practices

✅ Use *SSH-based tools (scp, sftp)* instead of unencrypted FTP.  
✅ Avoid using public Wi-Fi for sensitive transfers.  
✅ Set up *SSH key-based authentication* for automation.  
✅ Use *firewalls* and *strong passwords*.  
✅ Change the default SSH port for security.  

---

## 8. Summary

| Network Type | Example IP | Transfer Command | Speed | Security |
|---------------|-------------|------------------|--------|-----------|
| Same Network | 192.168.1.x | ⁠ scp file anand_bhardwaj@192.168.1.20:/path/ ⁠ | Fast | High |
| Different Network | 203.x.x.x (Public IP) | ⁠ scp file anand_bhardwaj@203.x.x.x:/path/ ⁠ | Depends on Internet | High |

---

## 9. Conclusion

File transfer over the *same network* is simple, fast, and requires only the local IP address.  
For *different networks*, the process involves a public IP, SSH configuration, and firewall permissions.  
Both methods can be made secure using *SSH encryption* and *key-based authentication*.

---