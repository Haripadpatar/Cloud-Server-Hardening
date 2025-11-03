# 🛡️ Cloud Server Hardening & Secure Access

**Student:** Haripad Patar  
**College:** Rungta College of Engineering & Technology  
**ERP ID:** 6604254  
**Semester:** 5th  
**Operating System:** Ubuntu Server 24.04 LTS  

---

## 📘 Overview
This project demonstrates the process of **hardening a cloud-hosted Linux server** for security and reliability.  
All configurations were performed on **Ubuntu Server 24.04 LTS** with the user `adminuser`.

---

## ⚙️ Security Configurations Implemented
- 🚫 **Disabled root SSH login**
- 🔥 **Enabled and configured UFW firewall**
  - Allowed only OpenSSH connections
- 🧱 **Installed and configured Fail2Ban**
  - Protects against brute-force SSH attacks
- 🕵️ **Set up Auditd** to monitor critical system files
- 🧩 **Verified sudo privileges and user permissions**

---

## 💻 Verification
All configurations were verified using the custom script `security-verify.sh`.

**Result:**  
✅ All hardening checks passed successfully.

---

## 📂 Files
| File | Description |
|------|--------------|
| `Cloud Server Hardening & Secure Access.pdf` | Detailed project report |
| `security-verify.sh` | Verification script (if applicable) |

---

## 🌐 Environment Setup
```bash
# Update system packages
sudo apt update && sudo apt upgrade -y

# Enable UFW firewall
sudo ufw allow OpenSSH
sudo ufw enable

# Disable root SSH login
sudo sed -i 's/^PermitRootLogin.*/PermitRootLogin no/' /etc/ssh/sshd_config
sudo systemctl restart ssh

# Install and enable Fail2Ban
sudo apt install fail2ban -y
sudo systemctl enable fail2ban
sudo systemctl start fail2ban

# Install Auditd
sudo apt install auditd -y
sudo systemctl enable auditd
sudo systemctl start auditd
