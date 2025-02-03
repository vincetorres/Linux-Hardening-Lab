# UFW Firewall Configuration

## Objective
To implement and document basic firewall rules using UFW on Kali Linux, ensuring that unnecessary and insecure ports are blocked while allowing essential traffic, and verifying the configuration.

## Steps

1. **UFW Enabled**
   - Ensure UFW is installed and enabled:
     ```bash
     sudo apt-get install ufw
     sudo ufw enable
     ```

2. **UFW Active**
   - Verify that UFW is active and running:
     ```bash
     sudo ufw status
     ```

3. **UFW Basic Rules Configured**
   - Block insecure ports (e.g., ports 20, 21, 23) and allow essential traffic (e.g., SSH, HTTP, HTTPS):
     ```bash
     sudo ufw deny 20
     sudo ufw deny 21
     sudo ufw deny 23
     sudo ufw allow ssh
     sudo ufw allow http
     sudo ufw allow https
     ```

4. **UFW Configuration Verified**
   - Confirm the UFW rules are configured correctly and active:
     ```bash
     sudo ufw status verbose
     ```

## Results
- UFW is active and enabled.
- Ports 20, 21, & 23 are blocked.

