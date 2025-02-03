# SSH Hardening Practice

## Overall Lab Aim
The aim of this lab is to enhance the security of SSH access by disabling insecure features such as password authentication, root login, and PAM. The lab also includes setting up public key authentication and configuring Fail2Ban to protect against brute-force login attempts.

---

# SSH Config File 

## Objective
Understand how to access and edit SSH configurations using the `sshd_config` file to enhance security by disabling password authentication, root login, and PAM.

## Steps

### 1. **Password Authentication Disabled**
   - Open the SSH configuration file for editing:
     ```bash
     sudo nano /etc/ssh/sshd_config
     # Disable password authentication
     PasswordAuthentication no
     ```
![sshd_config - Password Authentication Disabled](https://github.com/user-attachments/assets/ac03dc28-7847-4d0a-a242-6395c6ec9989)



### 2. **Root Login Disabled**
   - Disable root login via SSH:
     ```bash
     # Disable root login
     PermitRootLogin no
     ```
![sshd_config - Root Log In Disabled](https://github.com/user-attachments/assets/1b1d1a77-fd46-4746-84b9-5d08928dc7f2)

     

### 3. **UsePAM Disabled**
   - Disable Pluggable Authentication Module (PAM) for additional security:
     ```bash
     # Disable PAM
     UsePAM no
     ```
![sshd_config - UsePAM Disabled](https://github.com/user-attachments/assets/ae7b8d9b-2450-42de-aad7-e9b4a63078e1)

     

### 4. **Login Attempt from Another Machine**
   - Attempt to log in from another machine before and after applying changes to verify that root login is disabled and key-based authentication is enforced:
     ```bash
     # Test login with SSH from another machine
     ssh user@server_ip
     ```
![Before and After  Permission Denied](https://github.com/user-attachments/assets/16d1841e-5889-4a39-80cd-4fbae4826d58)

     

## Results
- Password authentication is disabled.
- Root login is disabled.
- Pluggable Authentication Module (PAM) is disabled.
- Login attempts from another machine show that root login is no longer allowed, and key-based authentication is enforced.

---

# Public Key Authentication Setup

## Objective
Set up public key authentication for SSH access to improve security.

## Steps

### 1. **Generate SSH Key Pair**
   - Generate a new SSH key pair:
     ```bash
     ssh-keygen -t rsa -b 4096
     ```

### 2. **Copy the Public Key to the Server**
   - Copy the public key to the server to enable key-based authentication:
     ```bash
     ssh-copy-id kali@192.168.64.3
     ```

## Results
- SSH key pair is generated.
- Public key has been copied to the server, enabling key-based authentication.

---

# Fail2Ban Setup

## Objective
Configure and enable Fail2Ban to prevent brute-force attacks by banning IP addresses with excessive failed login attempts.

## Steps

### 1. **Fail2Ban Enabled**
   - Install Fail2Ban and ensure it is enabled:
     ```bash
     sudo apt-get install fail2ban
     sudo systemctl enable fail2ban
     sudo systemctl start fail2ban
     ```

### 2. **Jail Configured**
   - Configure a Fail2Ban jail for SSH protection:
     ```bash
     sudo nano /etc/fail2ban/jail.local
     # Add the following to the file:
     [sshd]
     enabled = true
     port = ssh
     filter = sshd
     logpath = /var/log/auth.log
     maxretry = 3
     bantime = 600
     ```

### 3. **Configuration Verified**
   - Check the status of Fail2Ban and verify the SSH jail is active:
     ```bash
     sudo fail2ban-client status sshd
     ```

## Results
- Fail2Ban is installed and active.
- SSH jail is configured to protect against brute-force attacks.
- Configuration has been verified, and the jail is running.
