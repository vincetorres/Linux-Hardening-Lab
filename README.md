# Linux-Hardening-Lab

## Objective

The **Linux Hardening Lab** aimed to configure and implement security best practices on a Linux system, focusing on the hardening of SSH, configuring UFW (Uncomplicated Firewall), and setting up an Intrusion Detection System (IDS). The goal was to enhance the security posture of a Linux server by protecting it from unauthorized access, minimizing the attack surface, and ensuring that malicious activity could be detected. This hands-on lab was designed to deepen understanding of fundamental Linux security practices and reinforce practical skills for defending systems.

## Skills Learned

- **SSH Hardening**: Enforcing secure SSH configurations, disabling root login, and enforcing key-based authentication.
- **UFW Configuration**: Setting up a firewall to control inbound and outbound traffic based on specific security policies.
- **IDS Setup**: Implementing an Intrusion Detection System to detect and alert for malicious activities on the network.
- **Linux Security**: Gaining practical experience in hardening Linux systems to protect against unauthorized access and attacks.

## Tools Used

- **UFW (Uncomplicated Firewall)**: A tool used to configure firewall rules to secure the server.
- **SSH (Secure Shell)**: A protocol used to securely log into remote systems and execute commands.
- **Snort**: A widely-used IDS tool for detecting and alerting on network intrusions.
- **Syslog**: For monitoring and logging system activities and security events.
- **Wireshark**: A network protocol analyzer used to inspect network traffic.

## Steps

1. **Setting Up UFW (Uncomplicated Firewall)**:
   - **Objective**: Protect the system by controlling network access and allowing only necessary services.
   - **Steps**:
     - Install UFW:
       ```bash
       sudo apt install ufw
       ```
     - Enable UFW and configure default rules to deny incoming traffic and allow outgoing traffic:
       ```bash
       sudo ufw default deny incoming
       sudo ufw default allow outgoing
       ```
     - Allow SSH access and enable UFW:
       ```bash
       sudo ufw allow ssh
       sudo ufw enable
       ```
     - Verify UFW status:
       ```bash
       sudo ufw status
       ```

   ![Ref 1: UFW Configuration Screenshot](path_to_screenshot)  
   *This screenshot shows the UFW status after configuring the firewall, allowing only necessary traffic such as SSH.*

2. **Hardening SSH Configuration**:
   - **Objective**: Secure SSH access by disabling root login and enforcing key-based authentication.
   - **Steps**:
     - Modify the SSH configuration:
       ```bash
       sudo nano /etc/ssh/sshd_config
       ```
     - Set the following parameters:
       ```
       PermitRootLogin no
       PasswordAuthentication no
       ```
     - Restart the SSH service:
       ```bash
       sudo systemctl restart sshd
       ```

   ![Ref 2: SSH Configuration Screenshot](path_to_screenshot)  
   *This screenshot shows the modified SSH configuration with root login disabled and password authentication turned off, ensuring only key-based login.*

3. **Setting Up IDS (Intrusion Detection System)**:
   - **Objective**: Detect malicious network activity by implementing Snort IDS.
   - **Steps**:
     - Install Snort:
       ```bash
       sudo apt install snort
       ```
     - Configure Snort to monitor network traffic:
       ```bash
       sudo snort -A console -c /etc/snort/snort.conf -i eth0
       ```
     - Test Snort by generating some network traffic to see if it detects any unusual behavior.

   ![Ref 3: IDS Setup Screenshot](path_to_screenshot)  
   *This screenshot shows Snort running and monitoring network traffic, generating alerts for any suspicious activity.*

4. **Testing and Monitoring**:
   - **Objective**: Verify that all configurations are working as expected and monitor for security incidents.
   - **Steps**:
     - Monitor logs for any suspicious activity using `journalctl` or by reviewing Snort alerts.
     - Test the firewall by attempting unauthorized access and checking if the firewall blocks it.
     - Verify that Snort is generating alerts for potential intrusion attempts.

   ![Ref 4: IDS Monitoring Screenshot](path_to_screenshot)  
   *This screenshot shows Snort detecting an alert for suspicious network traffic, demonstrating the IDS functionality.*

---

## Final Notes

- **Challenges**: During setup, I encountered challenges configuring Snort properly and ensuring that UFW rules did not block essential services. Testing the firewall and IDS configurations helped troubleshoot these issues.
- **Future Improvements**: Further testing could include simulating different attack scenarios to ensure the IDS system can detect a variety of attack types. I also plan to explore more advanced IDS tools such as Suricata and integrate log aggregation for better monitoring.

