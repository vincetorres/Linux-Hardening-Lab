# IDS Setup (Snort)

## Objective
Install and configure Snort as an Intrusion Detection System (IDS) to monitor network traffic and detect potential security threats. This setup will include:
- Configuring a test ICMP rule to detect and log ICMP traffic.
- Verifying that Snort can successfully detect and alert on ICMP traffic in real-time.
- Reviewing the logged alerts to confirm proper functionality of the IDS.

## Steps

### 1. **Snort Installed**
   - Install:
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
     alert icmp any any -> any any (msg:"ICMP Echo Request Detected"; sid:1000001; rev:1;)
     ```
![Screenshot 2025-01-23 at 4 07 47 PM](https://github.com/user-attachments/assets/6f559cd4-f4f9-48c1-b644-e38c38cc91a6)


### 4. **Run Snort with ICMP Rule**
   - Run Snort with the ICMP rule configuration:
     
     ```bash
     snort -c /etc/snort/snort.lua -R /etc/snort/rules/local.rules
     ```
   - The `-R` flag specifies the path to the rule file (`local.rules`), ensuring that Snort uses the custom ICMP rule we added. This step confirms that the new rule does not interfere with Snort's operation and that the configuration is valid.

![Screenshot 2025-02-06 at 2 06 31 PM](https://github.com/user-attachments/assets/7e782220-6637-43e9-9fd9-6376f794f73c)



### 5. **Confirm Configuration**
   - Confirm that Snort ran the configuration with 0 warnings.

![Screenshot 2025-02-06 at 2 06 43 PM](https://github.com/user-attachments/assets/26c0992f-77da-409d-b252-cb792d7ce194)



### 6. **Run Snort with Alert Output**
   - Run Snort with the ICMP rule and enable fast alert output:
     
     ```bash
     sudo snort -c /etc/snort/snort.lua -R /etc/snort/rules/local.rules -i eth0 -A alert_fast
     ```
   - Here, we use the `-A alert_fast` option to enable fast alert output, which provides real-time alerts in a concise format. This is useful for immediate monitoring and debugging.


![Screenshot 2025-02-06 at 2 55 33 PM](https://github.com/user-attachments/assets/3519fb15-460a-44ae-b6d5-72f65aa615cf)




### 7. **Send ICMP Traffic**
   - Send ICMP traffic (e.g., ping) from another machine to trigger the Snort alert.


![Screenshot 2025-02-06 at 2 07 51 PM](https://github.com/user-attachments/assets/eaa5d24e-2016-4cde-97e9-04b6f0448613)



### 8. **Monitor Alerts**
   - Snort will display the corresponding alert pop-up while it is running.


![Screenshot 2025-02-06 at 2 08 04 PM](https://github.com/user-attachments/assets/3c407432-2091-4113-860d-f705b25c24a7)


### 9. **Review Logs**
   - When Snort is stopped (using `^C`), the report will show the alerts logged under detection.

![Screenshot 2025-02-06 at 2 08 55 PM](https://github.com/user-attachments/assets/44e780d6-ce21-4849-a1b4-181d021244dc)



## Results
- Snort is installed and running.
- ICMP traffic is being monitored by the configured rule.
- Alerts are output to a log file for review and analysis.
- ICMP traffic triggers alerts in real-time, and the alerts are logged for further investigation.
