# SSH Hardening Configuration


## Objective






Basic SSH Configurations 

## Objective
Understand how to access and edit SSH configurations using the `sshd_config` file to enhance security by disabling password authentication, root login, and PAM.

## Steps

1. **Password Authentication Disabled**
   - Open the SSH configuration file for editing:
     ```bash
     sudo nano /etc/ssh/sshd_config
     # Disable password authentication
     PasswordAuthentication no
     ```

2. **Root Login Disabled**
   - Disable root login via SSH:
     ```bash
     # Disable root login
     PermitRootLogin no
     ```

3. **UsePAM Disabled**
   - Disable Pluggable Authentication Module (PAM) for additional security:
     ```bash
     # Disable PAM
     UsePAM no
     ```

4. **Login Attempt from Another Machine**
   - Attempt to log in from another machine before and after applying changes to verify that root login is disabled and key-based authentication is enforced:
     ```bash
     # Test login with SSH from another machine
     ssh user@server_ip
     ```

## Results
- Password authentication is disabled.
- Root login is disabled.
- Pluggable Authentication Module (PAM) is disabled.
- Login attempts from another machine show that root login is no longer allowed, and key-based authentication is enforced.

