# 🔍 Wireshark Traffic Analysis – HTTP Credentials & File Download

This project analyzes a `.pcap` file that was originally labeled as FTP traffic. However, after investigation using Wireshark, it was discovered to be **HTTP-based**, involving credential leakage and a Windows update file download.

---

## 📂 Files

- `http-traffic-analysis.pcapng` – Captured network traffic

## 🎯 Objective

- Identify actual protocol behavior
- Extract any usernames, passwords, and IPs
- Confirm file download via HTTP

---

## ✅ Findings

| Field            | Value                                           |
|------------------|--------------------------------------------------|
| 👤 Username        | `anonymous`                                      |
| 🔐 Password        | `IEUser@`                                        |
| 📡 Source IP       | `81.131.67.131`                                  |
| 🎯 Destination IP  | `2001:638:902:1:201:2ff:fe3e:261d`              |
| 🌐 Protocol Used   | HTTP                                             |
| 📁 File Downloaded | `windowsxp-sp2-x86fre-en_us.exe` *(partial)*    |

---

## 🧠 Analysis Summary

Although the filename implied FTP traffic, Wireshark showed that the protocol used was actually **HTTP**. A username/password was found in cleartext, and an HTTP file download from Microsoft’s update server was captured in the traffic.

This is a great reminder to always **analyze the traffic, not the title**.

---

##  Tools Used

- **Wireshark**
- Filters used: `http`, `ip.addr == 81.131.67.131`, `http.request`

