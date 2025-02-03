# SSH Hardening Configuration

## Objective
To implement and document SSH hardening measures on Kali Linux, ensuring secure remote access by disabling root login, using key-based authentication, and enforcing strong security practices.

## Steps

1. **Disable Root Login**
   - Edit the SSH configuration file to disable root login via SSH:
     ```bash
     sudo nano /etc/ssh/sshd_config
     # Set PermitRootLogin to no
     PermitRootLogin no
     ```
   
2. **Enable SSH Key-Based Authentication**
   - Set up SSH key-based authentication and disable password authentication for enhanced security:
     ```bash
     sudo nano /etc/ssh/sshd_config
     # Ensure the following lines are set
     PasswordAuthentication no
     PubkeyAuthentication yes
     ```
   - Generate SSH key pair if not already done:
     ```bash
     ssh-keygen -t rsa
     ```
   - Copy the public key to the server:
     ```bash
     ssh-copy-id user@server_ip
     ```

3. **Change Default SSH Port**
   - Change the default SSH port from 22 to a custom port (e.g., 2222) to avoid automated attacks:
     ```bash
     sudo nano /etc/ssh/sshd_config
     # Set the Port to a non-default value
     Port 2222
     ```

4. **Restart SSH Service**
   - Apply the changes by restarting the SSH service:
     ```bash
     sudo systemctl restart ssh
     ```

5. **Verify SSH Configuration**
   - Verify that the SSH service is running with the updated configuration:
     ```bash
     sudo systemctl status ssh
     ```

## Results
- Root login has been disabled.
- SSH key-based authentication is enabled.
- Default SSH port has been changed to 2222.
