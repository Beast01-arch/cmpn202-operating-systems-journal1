
# 1. Introduction
The objective of Week 4 is to implement the Ubuntu Server system and foundational security controls required for secure remote administration. This part  focuses on SSH hardening, user privilege management, and firewall configure, ensuring that the server adheres to industry-standard security practices.
All configuration works in this part were performed remotely via SSH from the Fedora Workstation, in compliance with the administrative constraints defined in the coursework.
_________________________________________________________________________________
# 2. Secure Shell (SSH) Configuration
## 2.1 SSH Access Verification
ssh username @server_ip
Explanation:
This command make a secure remote shell session from the Fedora Workstation to Ubuntu Server. SSH serves as the exclusive administrative access mechanism for the server and workstation.

_________________________________________________________________________________
## 2.2 SSH Configuration File(Before Modification)
Sudo nano /etc/ssh/sshd_config
Explanation:
The SSH daemon configuration file is inspected to review and re-write default authentication and access settings prior to hardening.

_________________________________________________________________________________
## 2.3 SSH Hardening Configuration
The following settings were applied to harden SSH access:
PermitRootLogin no
PasswordAuthentication no
PubkeyAuthentication yes
Explanation:
•	Disable direct root login
•	Prevent password-based authentication
•	Enforce SSH key-based authentication
These controls significantly manage to reduce  the risk of brute-force and credential-based attacks.

_________________________________________________________________________________
## 2.4 SSH Service Restart
sudo systemctl restart ssh
Explanation:
Restarts the SSH service to apply configuration change.

_________________________________________________________________________________
## 2.5 SSH Configuration Verification
sudo systemctl status ssh
Explanation:
Confirms that the SSH service is active and running correctly after configuration change.

_________________________________________________________________________________
# 3. User and Privilege Management
## 3.1 Non-Root Administrative User Creation
sudo adduser adminuser
Explanation:
Creates a non-root user account for administrative task, enforcing the principle of least privilege.

_________________________________________________________________________________

## 3.2 Granting Administrative Privilege
sudo usermod -aG sudo adminuser
Explanation:
Adds the new client to the sudo group, allowing controlled privilege escalation when it require.

_________________________________________________________________________________
## 3.3 Verification of User Privileges
groups adminuser
Explanation:
Verifies that the client  has been correctly assigned administrative privilege.

________________________________________
# 4. Firewall Configuration
## 4.1 Firewall Installation and Enablement
sudo apt install ufw -y
sudo ufw enable
Explanation:
Installs and enables the Uncomplicated Firewall (UFW) to control incoming and outgoing traffics.

_________________________________________________________________________________
## 4.2 Restricting SSH Access to Workstation IP
sudo ufw allow from workstation_ip to port 22
Explanation:
Allows SSH access exclusively from the Fedora Workstation’s IP address, preventing unauthorised remote connection.

_________________________________________________________________________________
## 4.3 Default Deny Policy Enforcement
sudo ufw default deny incoming
sudo ufw default allow outgoing
Explanation:
Implements a default-deny security posture for incomming traffic, reducing the server attack surface.

_________________________________________________________________________________
## 4.4 Firewall Ruleset Verification
sudo ufw status verbose
Explanation:
Displays the complete firewall rule set, confirming correct enforcement of network access restriction.

_________________________________________________________________________________
# 5. Remote Administration Evidence
whoami
host_name
Explanation:
These commands confirm the authenticated client context and target system identity during remote administration.
📸 [SCREENSHOT PLACEHOLDER – Remote administration confirmation output]
_________________________________________________________________________________
# 6. Reflection
Week 4 established the foundational security posture of the  main Ubuntu Server system by  improved and enforcing secure remote access, restricting administrative privilege, and implementing host-based firewall control. These measures significantly reduce the system’s attack surface while maintaining operational accessibility.
By enforcing SSH key-based authentication and isolating administrative access to those workstations, the system now reflect professional-grade server security practice suitable for further monitoring, testing, and optimisation.

