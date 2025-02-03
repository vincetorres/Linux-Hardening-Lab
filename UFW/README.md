# UFW (Uncomplicated Firewall) Configuration

## Objective
The goal of this section is to configure UFW to secure the Linux server by defining inbound and outbound traffic rules. UFW simplifies managing a firewall on Linux and enhances the system's security by restricting unauthorized network access.

## Steps

### 1. **Install UFW**
   - First, ensure that UFW is installed on your system:
     ```bash
     sudo apt-get install ufw
     ```

### 2. **Enable UFW**
   - Enable UFW to start managing firewall rules:
     ```bash
     sudo ufw enable
     ```

### 3. **Configure UFW Rules**
   - **Allow SSH Access**: Allow incoming SSH connections to avoid locking yourself out:
     ```bash
     sudo ufw allow ssh
     ```
   - **Allow Specific Ports**: For example, allow HTTP (port 80) and HTTPS (port 443):
     ```bash
     sudo ufw allow http
     sudo ufw allow https
     ```
   - **Deny All Other Incoming Connections**: By default, UFW denies all incoming traffic unless explicitly allowed:
     ```bash
     sudo ufw default deny incoming
     ```
   - **Allow Outgoing Connections**: Allow all outgoing traffic:
     ```bash
     sudo ufw default allow outgoing
     ```

### 4. **Check UFW Status**
   - After configuring the firewall rules, check the status of UFW to verify the applied rules:
     ```bash
     sudo ufw status verbose
     ```

### 5. **Logging**
   - Enable UFW logging to monitor traffic:
     ```bash
     sudo ufw logging on
     ```

## Tools Used
- **UFW (Uncomplicated Firewall)**: A simple and effective tool for managing firewall rules and improving system security.

## Screenshot Examples
*Ref 1: UFW Status Screenshot*
- Shows the UFW status with active rules and allowed services.

*Ref 2: UFW Command Screenshot*
- Displays the UFW commands used to allow SSH, HTTP, and HTTPS traffic.

