Linux iMac CPU Investigation 🐧🔧

A small hands-on investigation of an Apple iMac 11,3 running Linux Mint Cinnamon.

The purpose of this project is to explore how the system behaves under Linux and to better understand the hardware, kernel, CPU frequency scaling, storage health, boot process and basic system performance.

This is an experimental and educational project rather than a formal hardware benchmark.

🖥️ System
Component	Information
Computer	Apple iMac 11,3
Operating System	Linux Mint Cinnamon
Kernel	Linux 7.0.0-34-generic
CPU	Intel Core i3-550
CPU cores	2
CPU threads	4
Maximum CPU frequency	3.192 GHz
Minimum CPU frequency	1.197 GHz
CPU frequency driver	acpi-cpufreq
Storage	1 TB Seagate Barracuda 7200.12
Filesystem	ext4
🔍 What Was Investigated

The investigation included:

- Linux kernel information

- Apple EFI and hardware identification

- CPU identification and capabilities

- CPU frequency scaling

- CPUFreq governors

- CPU behavior under load

- System boot performance

- systemd startup services

- Storage device health using SMART

- Basic CPU workload testing

⚙️ CPU Frequency Scaling

Linux initially used the following CPUFreq governor:

schedutil


The available governors were:

conservative
ondemand
userspace
powersave
performance
schedutil


For testing, the CPU governor was temporarily changed to:

performance


This did not overclock the processor.

Instead, it instructed Linux to favor higher CPU performance states.

The processor's configured frequency limits remained:

Minimum: 1.197 GHz
Maximum: 3.192 GHz

🧪 CPU Frequency Test

During CPU load, the following value was observed:

scaling_cur_freq = 3192000


The configured maximum was:

scaling_max_freq = 3192000


Therefore:

3,192,000 kHz = 3.192 GHz


The CPU successfully reached its configured maximum operating frequency.

💻 Simple CPU Workload

A simple Bash workload was used:

time for i in {1..5000000}; do :; done


Result:

real    0m11.783s
user    0m11.097s
sys     0m0.684s


This is not intended to be a formal CPU benchmark. Bash itself contributes significantly to the execution time.

The test was primarily used to generate CPU activity while observing frequency behavior.

💾 Storage Investigation

The system drive was identified as:

Seagate Barracuda 7200.12
ST31000528AS
1 TB
7200 RPM


SMART health reported:

SMART overall-health self-assessment test result: PASSED


Important SMART attributes included:

Reallocated sectors:        0
Pending sectors:            0
Offline uncorrectable:      0
Reported uncorrectable:     0
UDMA CRC errors:            0


No errors were recorded in the SMART error log.

🧠 Kernel Investigation

The Linux kernel identified the machine as:

Apple Inc. iMac11,3
Mac-F2238BAE


The system firmware was identified as Apple EFI.

The CPU was detected as:

Intel(R) Core(TM) i3 CPU 550 @ 3.20GHz


The system contains four populated memory slots.

Secure Boot was reported as disabled.

🚀 Boot Investigation

System startup was also investigated using:

systemd-analyze


and:

systemd-analyze blame


The purpose was to understand where time was spent during system startup rather than blindly disabling services.

The system had already been optimized before this investigation, so no unnecessary service changes were made as part of this project.

🧪 Philosophy

The main idea behind this project is simple:

Understand first. Change second.

Instead of applying random "performance tweaks", the system was inspected using Linux's own diagnostic tools.

Changes were kept temporary whenever possible, and measurements were taken before drawing conclusions.

📄 Report

The detailed English report is available here:

CPU Performance and Frequency Test Report

The report documents the CPU frequency experiment and its results in more detail.

🐧 Why This Project Exists

This project started from simple curiosity:

What is this old iMac actually doing when Linux is running on it?

The investigation gradually turned into a hands-on exploration of the Linux kernel, hardware detection, CPU frequency scaling, storage health and system startup.

The goal is not to make the machine something it is not.

The goal is to understand it.

⚠️ Disclaimer

This is a personal educational experiment performed on older hardware.

The results are specific to this particular iMac and software configuration and should not be treated as general benchmark results for the Intel Core i3-550 or Apple iMac systems.

No hardware-level CPU overclocking was performed during this investigation.

System: Apple iMac 11,3
OS: Linux Mint Cinnamon
CPU: Intel Core i3-550
Project type: Personal Linux / hardware investigation
