# UFW Firewall Configuration

## Objective
To implement and document basic firewall rules using UFW on Kali Linux, ensuring that unnecessary and insecure ports are blocked and verifying the configuration.

## Steps

1. **UFW Enabled**
   - Ensure UFW is installed and enabled:
     ```bash
     sudo apt-get install ufw
     sudo ufw enable
     ```
![1  UFW enabled](https://github.com/user-attachments/assets/25c6d1f8-1cec-49ac-8b81-1b002c74b59b)


     

2. **UFW Active**
   - Verify that UFW is active and running:
     ```bash
     sudo ufw status
     ```
![2  UFW active](https://github.com/user-attachments/assets/b8e7bcb3-fa1d-4801-b3ab-1b3b79c67ba5)


     

3. **UFW Basic Rules Configured**
   - Block insecure ports (e.g., ports 20, 21, 23)
     ```bash
     sudo ufw deny 20
     sudo ufw deny 21
     sudo ufw deny 23
     ```

![3  UFW Basic rules configured](https://github.com/user-attachments/assets/39a930a8-2aa7-41fb-99ac-3f4bbd78dcec)


     

4. **UFW Configuration Verified**
   - Confirm the UFW rules are configured correctly and active:
     ```bash
     sudo ufw status numbered
     ```

![4  UFW Configuration verified](https://github.com/user-attachments/assets/dcf6ff07-931c-4863-a818-c7468180dd52)


     

## Results
- UFW is active and enabled.
- Ports 20, 21, & 23 are blocked.
