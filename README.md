# Linux-Hardening-Lab

## Objective

Aimed to configure and implement security practices on a Linux system, focusing on the hardening of SSH, configuring UFW, and setting up an Intrusion Detection System. This hands-on lab was designed to deepen understanding of fundamental Linux security practices and reinforce practical skills for defending systems.

## Skills Learned

- **SSH Hardening**: Enforcing secure SSH configurations, disabling root login, and enforcing key-based authentication.
- **UFW Configuration**: Setting up a firewall to control inbound and outbound traffic based on specific security rules.
- **IDS Setup**: Implementing an Intrusion Detection System to detect and alert 
- **Linux Security**: Gaining practical experience in hardening Linux systems

## Tools Used

- **UFW (Uncomplicated Firewall)**: A tool used to configure firewall rules to secure the server.
- **SSH (Secure Shell)**: A protocol used to securely log into remote systems and execute commands.
- **Snort**: A widely-used IDS tool for detecting and alerting on network intrusions.
- **Fail2Ban**: A log-parsing tool that automatically blocks IPs making multiple failed login attempts, protecting services such as SSH from brute force attacks.

## Steps

1. **Setting Up UFW (Uncomplicated Firewall)**
2. **Hardening SSH Configuration**
3. **Setting Up IDS (Intrusion Detection System)**:
4. **Testing and Monitoring**:

## Final Notes

- **Challenges**: During setup, I encountered challenges configuring Snort properly and ensuring that UFW rules did not block essential services. Testing the firewall and IDS configurations helped troubleshoot these issues.
- **Future Improvements**: Further testing could include simulating different attack scenarios to ensure the IDS system can detect a variety of attack types. I also plan to explore more advanced IDS tools such as Suricata and integrate log aggregation for better monitoring.

