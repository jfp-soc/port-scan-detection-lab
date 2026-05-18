# Port Scan Detection Engineering Lab

## Objective
Simulate port scanning activity and observe network indicators for SOC detection engineering purposes.

## Lab Setup
- Kali Linux (attacker / scanner)
- VirtualBox networking (NAT / host-only environment)
- Target: 10.0.2.2 (Virtual network host)

## Tools Used
- Nmap
- tcpdump

## Methodology

### 1. Host discovery
```bash
nmap 10.0.2.0/24
```

### 2. Service enumeration
```bash
nmap -sV 10.0.2.2
```

### 3. Full port scan
```bash
nmap -p- -T4 10.0.2.2
```

### 4. SYN scan generation
```bash
nmap -sS 10.0.2.2
```

### 5. Traffic capture
```bash
tcpdump -i eth0
```

## Key Findings

- Multiple open TCP ports identified (5000, 7000, 64487+)
- High volume scan activity generated measurable network traffic
- SYN scanning produced distinct packet patterns observable in tcpdump
- Packet capture recorded:
  - 1809 packets captured
  - 131115 packets processed
  - Kernel packet drops occurred due to traffic volume

## Detection Insights

- Port scans create identifiable traffic spikes
- SYN packets are key indicators of reconnaissance activity
- Full port scans generate high noise and are easily detectable

## Conclusion

This lab demonstrates how reconnaissance activity appears at the network level and provides baseline understanding for building detection rules in a SOC environment.

## Evidence

### Service Scan
![service scan](screenshots/scan1.png)

### Full Port Scan
![full scan](screenshots/scan2.png)

### Packet Capture
![tcpdump](screenshots/scan3.png)
