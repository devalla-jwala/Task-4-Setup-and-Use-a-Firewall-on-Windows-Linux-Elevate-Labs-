# Task-4-Setup-and-Use-a-Firewall-on-Windows-Linux-Elevate-Labs-
   Firewall configuration, network traffic filtering, ports, UFW, Windows Firewall

This task is part of my cybersecurity internship. I configured and tested a firewall using **UFW (Uncomplicated Firewall)** on **Kali Linux** to block insecure services (Telnet) and allow secure connections (SSH). I validated the configuration using Telnet and documented all commands and results.

---

## Tools & Environment

- **Tool:** UFW (Uncomplicated Firewall)  
- **OS:** Kali Linux  
- **Testing Tool:** Telnet  

---

## Step 1: Enable UFW

Opened terminal and ran:

```bash
sudo ufw enable
```

UFW was successfully enabled and started applying default rules.

![image alt](https://github.com/devalla-jwala/Task-4-Setup-and-Use-a-Firewall-on-Windows-Linux-Elevate-Labs-/blob/f3248061f9d00714052ec2c9ea32ab39bc1097eb/1.png)
---

##  Step 2: Block Port 23 (Telnet)

Ran the following command to block insecure Telnet access:

```bash
sudo ufw deny 23
```

This blocks any inbound traffic to port 23 (IPv4 and IPv6).

![image alt](https://github.com/devalla-jwala/Task-4-Setup-and-Use-a-Firewall-on-Windows-Linux-Elevate-Labs-/blob/f3248061f9d00714052ec2c9ea32ab39bc1097eb/2.png)
---

##  Step 3: Allow Port 22 (SSH)

Allowed secure remote access via SSH:

```bash
sudo ufw allow 22
```

This ensures that SSH connections are permitted.


![image alt](https://github.com/devalla-jwala/Task-4-Setup-and-Use-a-Firewall-on-Windows-Linux-Elevate-Labs-/blob/f3248061f9d00714052ec2c9ea32ab39bc1097eb/3.png)


---

##  Step 4: Check Firewall Rules

Listed all firewall rules:

```bash
sudo ufw status numbered
```


###  Output:
```bash
Status: active

[ 1] 23                         DENY IN     Anywhere
[ 2] 22                         ALLOW IN    Anywhere
[ 3] 23 (v6)                    DENY IN     Anywhere (v6)
[ 4] 22 (v6)                    ALLOW IN    Anywhere (v6)
```



![image alt](https://github.com/devalla-jwala/Task-4-Setup-and-Use-a-Firewall-on-Windows-Linux-Elevate-Labs-/blob/f3248061f9d00714052ec2c9ea32ab39bc1097eb/4.png)


---

##  Step 5: Test Telnet Blocking

### A. Install Telnet

```bash
sudo apt install telnet
```

![image alt](https://github.com/devalla-jwala/Task-4-Setup-and-Use-a-Firewall-on-Windows-Linux-Elevate-Labs-/blob/f3248061f9d00714052ec2c9ea32ab39bc1097eb/5.png)


### B. Attempt to connect:

```bash
telnet localhost 23
```

🧪  Result:
```bash
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused
```

This confirms port 23 is blocked by the firewall.

![image alt](https://github.com/devalla-jwala/Task-4-Setup-and-Use-a-Firewall-on-Windows-Linux-Elevate-Labs-/blob/f3248061f9d00714052ec2c9ea32ab39bc1097eb/6.png)

---

## 🧹 Step 6: Remove Port 23 Rule (Cleanup)

Checked current rule numbers:

```bash
sudo ufw status numbered
```

![image alt](https://github.com/devalla-jwala/Task-4-Setup-and-Use-a-Firewall-on-Windows-Linux-Elevate-Labs-/blob/f3248061f9d00714052ec2c9ea32ab39bc1097eb/7.png)

Deleted port 23 rules (both v4 & v6):

```bash
sudo ufw delete 1
sudo ufw delete 3
```

![image alt](https://github.com/devalla-jwala/Task-4-Setup-and-Use-a-Firewall-on-Windows-Linux-Elevate-Labs-/blob/f3248061f9d00714052ec2c9ea32ab39bc1097eb/8.png)

This restored the firewall to its original state.

---

## ✅ Step 7: Final Rule Check

Ran final verification:

```bash
sudo ufw status numbered
```

### 📌 Output:
```bash
Status: active

[ 1] 22                         ALLOW IN     Anywhere
[ 2] 22 (v6)                    ALLOW IN     Anywhere (v6)
```

Only SSH (port 22) is allowed.

![image alt](https://github.com/devalla-jwala/Task-4-Setup-and-Use-a-Firewall-on-Windows-Linux-Elevate-Labs-/blob/f3248061f9d00714052ec2c9ea32ab39bc1097eb/9.png)

---

