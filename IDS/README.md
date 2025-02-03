# IDS Setup (Snort)

## Objective
Install and configure Snort as an Intrusion Detection System (IDS) to monitor network traffic and detect potential security threats. The setup will include configuring a test ICMP rule and setting up alert output for notification.

## Steps

### 1. **Snort Installed**
   - Install Snort on the system:
     ```bash
     sudo apt-get update
     sudo apt-get install snort
     ```
     ![Screenshot 2025-01-23 at 1 50 22 PM](https://github.com/user-attachments/assets/48e7e675-4c3f-4489-bdc7-2e955d2ea219)


### 2. **Snort Running**
   - Run Snort with the specific configuration and interface (replace `eth0` with your network interface):
     ```bash
     snort -c /etc/snort/snort.lua -i eth0
     ```
![Screenshot 2025-01-23 at 3 42 43 PM](https://github.com/user-attachments/assets/65653cb9-c1d1-4826-9dc3-9350ec6ea784)



### 3. **ICMP Rule Config**
   - Configure Snort to monitor ICMP traffic by editing the rules file:
     ```bash
     sudo nano /etc/snort/rules/local.rules
     # Add an ICMP rule to monitor ICMP traffic
     alert icmp any any -> any any (msg:"ICMP traffic detected"; sid:1000001;)
     ```
![Screenshot 2025-01-23 at 4 07 47 PM](https://github.com/user-attachments/assets/6f559cd4-f4f9-48c1-b644-e38c38cc91a6)

     

### 4. **Alert Output Config**
   - Configure Snort's alert output in `snort.lua`:
     ```bash
     sudo nano /etc/snort/snort.lua
     # Configure the alert output settings
     alert_fast = {
         file = true
         filename = '/var/log/snort/alert'
     }
     ```

![Screenshot 2025-01-28 at 3 40 27 PM](https://github.com/user-attachments/assets/5aa96693-b954-46fe-9d42-843b3617cb42)

     

## Results
- Snort is installed and running.
- ICMP traffic is being monitored by the configured rule.
- Alerts are output to a log file for review and analysis.
