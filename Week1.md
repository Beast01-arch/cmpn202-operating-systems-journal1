# 1.	Introduction
The aim of Week 1 is to design and document the basic architecture of the operating system environment, which will be configured, secured, and tested throughout this coursework. This phase, therefore, deals with planning and justification, ensuring all decisions made are justified and appropriate, just as in the Linux server environment."
The design of the system includes the use of a dual system approach, comprising of a Linux server and an admin workstation. Of course, just like in an actual data center or cloud computing system, server management is not done directly.
___________________________________________________________________________
# 2.	System Architecture Overview
The architecture used in the deployment includes two virtual machines running on the same machine:
•	Workstation System: Fedora Work
•	Server System: Ubuntu Server (Headless)
Fedora Workstation will serve as the administrative control system, with Ubuntu Server being the target system on which we will perform configuration, hardening, and benchmarking tasks.
All administrative tasks shall only be conducted over SSH connections and thus require Linux command-line skills.
Architectural Rationale
This architecture requires:
•	Independence between the concerns of administration and service hosting
•	Secure remote management practices
•	Ending dependence on graphical user interfaces in production servers
•	Realistic simulation of typical server management tasks
A diagram of the system architecture, reflecting the virtual machines and the networking, is presented in the journal.
___________________________________________________________________________
# 3.	Server Distribution Choice and Rationale
Chosen Server Operating System: Ubuntu Server (LTS).
For the server operating system, Ubuntu Server was chosen because of the following reasons:
• Long-Term Support (LTS): Offers prolonged security updates and stability, which is a must for production-grade scenarios
•	Comprehensive Documentation: Official and community resources make it easy to understand and identify errors
• Industry Adoption: Industry-wide adoption in cloud computing and enterprise environments
• Package Management: APT offers an excellent and stable package management system
•	Security Maintenance: Maintenance updates fix known security problems, minimizing vulnerability to threats.
Comparison with Alternatives
• Debian: While Debian is very stable, it favors conservative updates that may slow down exposure to new functionality necessary for performance testing
•	RHEL-based Systems: While these systems are certainly enterprise-class, the lifecycle phase changes might add complexity for an environment intended for learning
Ubuntu Server is therefore the best example of a combination of stability, usability, security, and market relevance.
___________________________________________________________________________
# 4.	Workstation Configuration Decision
Chosen Workstation: Fedora Workstation
Fedora Workstation was picked as the administrative workstation because of the following reasons:
•	Modern Linux Environment: Offers a contemporary toolset and kernel environment.
•	Excellent Developer Tools: Comes with great terminal, SSH client, and writing scripts environment
•	SELinux Exposure: The Fedora operating system is used with SELinux enabled by default. The SELinux exposure is an opportunity to gain experience with
•	Separation of Duties from Server Role: This is a measure that ensures that administrative tasks are carried out outside of server role responsibilities
Use of Fedora as workspace emphasizes the administrative work process with a focus on never having access to servers from graphical interfaces.
 
___________________________________________________________________________
# 5.	 Network Configuration Documentation
Both virtual machines are connected in a VirtualBox Virtual Network and facilitate controlled and isolated communication between the workstation and server.
Network Design Characteristics:
•	Both systems are hosted on the same virtual network
•	The server is only accessible through the workstation
•	Network Isolation to Prevent Unintentional Exposure
•	IP addressing is also referenced as supporting firewall and SSH constraints in subsequent stages
This setup enables compliance with both ethical and security concerns while facilitating necessary SSH administrations.
___________________________________________________________________________
# 6.	System Specification Collection (CLI Evidence)
For a general idea of the server environment, the system specifications were determined through the use of standard Linux command-line tools.
Purpose
These commands offer proof of the following:
•	Cache memory
•	Kernel and architecture information
•	Disk Capacity and Usage
•	Network interface configuration
•	Operating system version

 
__________________________________________________________________________
# 7.	 Comm and-Line Evidence (Ubuntu Server)
These are the commands that were performed on the Ubuntu Server, and their screenshots are shown below:
## 7.1	Kernel and Architecture Information
uname -a
Purpose:
Prints kernel version and architecture information, as well as OS details, verifying the server environment.
![week 1 – username (uname)](img/week1/uname)
________________________________________________________________________
## 7.2	Memory Information
free -h
Purpose:
Displays the total, used, and available memory details, which helps set the baseline for available RAM.
________________________________________________________________________
## 7.3	Disk Usage Information
df -h
Purpose:
Shows disk use and mounted file systems, allowing the user to evaluate storage space for applications and logs.
________________________________________________________________________
## 7.4	Network Interface Configuration
ip addr
Aim:
Provides lists of network interfaces and assigned IP addresses, serving as the foundation for implementing SSH security restrictions.
________________________________________________________________________
## 7.5	Operating System Distribution Information
lsb_release -
PURPOSE:
Confirms the Ubuntu Server version and release information.
________________________________________________________________________
# 8. Reflection (Professional Insight)
From Week 1, the system architecture is well defined and justified. It emphasizes security, realism, and command line skills. Through careful selection of distributions and strict remote administration, this environment is ready for secure configuration, monitoring, and performance analysis in the next weeks.
This is an important planning stage that ensures that all future technical decisions are founded on a transparent and professionally justified basis.

