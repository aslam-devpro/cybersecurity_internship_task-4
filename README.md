# 🛡️ Cybersecurity Internship - **Task 4**

## 🔧 Setup and Use a Firewall on Linux (Kali)

📅 **Date Performed:** Aug 16, 2025

🧰 **Tool Used:** UFW (Uncomplicated Firewall)

💻 **System:** Kali Linux


## ⚙️ Configuration Overview

| Step | Action                                                               |
| ---- | -------------------------------------------------------------------- |
| 1️⃣  | Installed and enabled UFW                                            |
| 2️⃣  | Listed current firewall rules (baseline)                             |
| 3️⃣  | Added rule to **block** inbound traffic on port **23** (Telnet)      |
| 4️⃣  | Tested the rule using `telnet localhost 23` – **Connection refused** |
| 5️⃣  | Added rule to **allow** inbound **SSH** (port 22)                    |
| 6️⃣  | Removed the temporary Telnet block rule                              |
| 7️⃣  | Verified final firewall configuration                                |



## ✅ Commands Used

```bash
# Install and enable UFW
sudo apt update
sudo apt install ufw
sudo ufw enable

# List current rules
sudo ufw status numbered

# Block Telnet (port 23)
sudo ufw deny 23
sudo ufw status numbered

# Test the rule
telnet localhost 23

# Allow SSH (port 22)
sudo ufw allow 22
sudo ufw status numbered

# Remove Telnet block rule (note: rule numbers may change)
sudo ufw delete <rule_number_of_23>
sudo ufw delete <rule_number_of_23 (v6)>
sudo ufw status numbered
```


## 🔎 Result & Verification

| Port   | Rule                    | Status                   |
| ------ | ----------------------- | ------------------------ |
| **23** | Deny inbound            | ✅ Blocked (tested)       |
| **22** | Allow inbound (SSH)     | ✅ Allowed                |
| —      | Default incoming policy | ❌ Deny all other traffic |

> ✔️ **Telnet connection attempt was rejected.**

> ✔️ **SSH remained accessible after rule changes.**


## 📷 Screenshots

Screenshots are uploaded into the folder firewall_configuration


## 📌 Notes

* UFW acts as a packet filter and decides whether to **allow** or **deny** traffic based on IP address, port and protocol.
* Kali’s default UFW policy is **deny incoming, allow outgoing**.
* Port-specific rules override the default policy.
* Always remove test rules after verifying to maintain a secure and clean configuration.

