
# Overview
During Week 2, command-line (Security Planning & Testing Preparation) tools are used only for inspection, verification, and planning. No permanent security configuration changes are required at this stage. The purpose of these commands is to observe the current system state, validate assumptions, and support the design of the security baseline and performance testing methodology.
All commands in this section were executed on the Ubuntu Server system.
________________________________________
# 1. System Process Overview (Baseline Observation)
top
Explanation:
This command provides a real-time view of running processes, CPU utilisation, memory usage, and system load averages. It is used during Week 2 to observe baseline system behaviour prior to workload execution.

________________________________________
# 2. System Load and Uptime Verification
uptime
Explanation:
This command displays system uptime and load averages over 1, 5, and 15 minutes. These values establish a baseline reference for later performance comparisons under load.

________________________________________
# 3. Memory Usage Snapshot
free -h
Explanation:
This command reports current memory usage in a human-readable format. Observing memory availability at this stage supports the planning of memory-intensive workload testing.

________________________________________
# 4. Disk Usage and Filesystem Overview
df -h
Explanation:
This command displays mounted filesystems and available disk capacity. It informs storage planning and identifies potential disk constraints prior to I/O performance testing.
]
________________________________________
# 5. Network Interface and IP Address Verification
ip addr
Explanation:
This command lists network interfaces and assigned IP addresses. The output is used to plan firewall restrictions, SSH access controls, and network performance testing scenarios.

________________________________________
# 6. Active Network Services and Listening Ports
ss -tuln
Explanation:
This command displays all listening TCP and UDP ports. Identifying active services supports the network security checklist and helps minimise the system’s attack surface.

________________________________________
# 7. User Account Enumeration
cut -d: -f1 /etc/passwd
Explanation:
This command lists all user accounts on the system. Reviewing user accounts is essential for planning least-privilege access controls and administrative role separation.

________________________________________
# 8. Current Logged-In Users
who
Explanation:
This command displays currently logged-in users. It is used to confirm administrative access patterns and ensure no unauthorised sessions are present.

________________________________________
# 9. Installed Security Update Mechanism Check
systemctl status unattended-upgrades
Explanation:
This command checks whether automatic security updates are installed or active. The result informs later configuration decisions related to patch management.

________________________________________
# 10. Mandatory Access Control Status (Pre-Configuration)
aa-status
Explanation:
This command checks the current AppArmor status on the system. Observing enforcement and loaded profiles provides a baseline for later access control implementation.

________________________________________
# 11. SSH Service Status Verification
systemctl status ssh
Explanation:
This command verifies that the SSH service is active. SSH is the primary remote administration mechanism and must be operational for subsequent coursework phases.

________________________________________
#  Summary of = Commands
The commands executed during Week 2 focus on system observation rather than configuration. Collectively, they provide:
•	Baseline performance metrics
•	Visibility into running services
•	Network exposure awareness
•	User and access context
•	Security mechanism readiness
This evidence supports the development of a measurable security baseline and a structured performance testing methodology, ensuring informed and defensible system configuration in later weeks

