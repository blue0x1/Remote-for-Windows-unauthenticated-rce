Exploit Title: Remote for Windows 2024.15 -  unauthenticated RCE <br>
Date: 2025-05-19 <br>
Exploit Author: Chokri Hammedi <br>
Vendor Homepage: https://rs.ltd <br>
Software Link: https://rs.ltd/latest.php?os=win <br>
Version: 2024.15 <br>
Tested on: Windows 10/11 with Remote for Windows (helper) <br>

<br>

**This remote code execution works when the "ask to grant access for unknown iOS devices" in settings is unchecked**
<br>
<br>
The Remote for Windows helper service exposes unauthenticated RCE through the executeScript API endpoint.
This allows SYSTEM-level command execution via crafted HTTP requests.

**Identification:** <br>
```bash
nmap -p- -T4 <target> --script ssl-cert
```

Look for SSL cert with subject: ```CN=SecureHTTPServer/O=Evgeny Cherpak/C=US```

![image](https://github.com/user-attachments/assets/81885f65-571c-45ea-a7e9-41b587b13640)

**Usage:** <br>
```bash
python exploit.py <target_ip> <port> "<command>"
```

**Example:**
<br>

![image](https://github.com/user-attachments/assets/b975b333-8e1e-4e48-b18f-e86576065d84)
