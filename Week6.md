
# 1.	 Introduction
In this we will evaluate the performance characteristics of the Ubuntu Server operating system under different workload condition. This part focuses on quantitative performance measurement, bottleneck identification, and performance optimisation, enabling a deeper understanding of how operating system resource are allocated and managed.
All performance testing was conducted on the Ubuntu Server, with monitoring performed remotely from the Fedora Workstation using SSH way.
___________________________________________________________________________
# 2.	 Testing Methodology
Performance testing was conducted using a structured methodology to ensure repeatability and accuracy.
Testing Scenarios
•	Baseline (idle system)
•	Application load testing
•	Bottleneck identification
•	Optimisation testing and comparison
Metrics Collected
•	CPU utilisation
•	Memory usage
•	Disk I/O performance
•	Network throughput and latency
•	System load averages
•	Service response behaviour
___________________________________________________________________________
# 3.	Baseline Performance Measurement
Baseline measurements were recorded with no active workload to establish a reference point.
uptime
free -h
df -h
top
Explanation:
These commands provide baseline CPU load, memory usage, disk availability, and process activity prior to workload execution.

___________________________________________________________________________
# 4.	CPU and Memory Load Testing
## 4.1 CPU Stress Test
stress-ng --cpu 4 --timeout 60s
Explanation:
Generates sustained CPU load to evaluate scheduling behaviour, CPU saturation, and system responsiveness.

___________________________________________________________________________
## 4.2 Memory Stress Test
stress-ng --vm 2 --vm-bytes 80% --timeout 60s
Explanation:
Allocates a significant portion of system memory to observe memory pressure handling and potential swapping behaviour.

___________________________________________________________________________
# 5.	Disk I/O Performance Testing
fio --name=io_test --rw=readwrite --bs=4k --size=1G --numjobs=1 --time_based --runtime=60
Explanation:
Simulates real-world disk read/write workloads to assess I/O throughput and latency.

___________________________________________________________________________
# 6.	Network Performance Testing
Testing network performance between a server and workstation involves measuring key metrics such as throughput, latency, jitter, packet loss, and reliability to ensure optimal data transfer efficiency.
## 6.1 Starting iperf Server (Ubuntu Server)
iperf3 -s

___________________________________________________________________________
## 6.2 Running iperf Client (Fedora Workstation)
iperf3 -c 192.168.56.101
Explanation:
Measures network throughput and latency between the workstation and the server.

___________________________________________________________________________
# 7.	Bottleneck Identification
Performance analysis revealed the following bottlenecks:
•	CPU saturation under sustained load
•	Increased memory pressure during memory-intensive workloads
•	Elevated disk I/O wait during simultaneous read/write operations
These observations guided the optimisation strategies applied in the next phase.
_________________________________________________________________________________
# 8.	Optimisation Testing
## 8.1 Optimisation Example – Reducing Unnecessary Services
systemctl list-unit-files --type=service
sudo systemctl disable apache2
Explanation:
Disabling unused services reduces background resource consumption and improves system efficiency.

_________________________________________________________________________________
## 8.2 Post-Optimisation Performance Re-Test
Baseline and load tests were repeated after optimisation to quantify improvements.

___________________________________________________________________________
# 9.	Performance Analysis Summary
Post-optimisation results demonstrated:
•	Reduced CPU load averages
•	Improved memory availability
•	Lower disk I/O latency
•	Improved overall system responsiveness
Quantitative data was recorded and visualised using tables and charts.
___________________________________________________________________________
# 10.	Reflection 
It demonstrated how operating system performance is influenced by workload characteristics and configuration choices. Through systematic testing and optimisation, measurable improvements were achieved, highlighting the trade-offs between performance, service availability, and resource utilisation.

