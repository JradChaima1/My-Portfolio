## Intercepting and Interpreting Network Traffic with Packet Sniffing Tools 
## Activities Performed

### 1. Capturing Network Traffic with Wireshark

- Opened Wireshark on a Kali Linux system.
- Selected the appropriate network interface (eth0).
- Generated network traffic by accessing NeverSSL website through Firefox.
- Captured and analyzed packets in real time.

<img width="1122" height="446" alt="Pasted image 20260531195402" src="https://github.com/user-attachments/assets/c481de11-b4e0-4fcc-9e03-44e867691247" />


### 2. Analyzing the TCP Three-Way Handshake

- Identified the TCP connection establishment process.
- Observed:
    - SYN packet
    - SYN-ACK packet
    - ACK packet

<img width="1346" height="97" alt="Pasted image 20260603214143" src="https://github.com/user-attachments/assets/fe27753d-ca9f-41f2-abe2-c33f93f2beb2" />


- Verified successful TCP session establishment between client and server.

### 3. Examining Packet Details

- Analyzed packet information across Wireshark panes.
- Reviewed:

    - **Source and destination IP addresses**

<img width="1019" height="57" alt="Pasted image 20260603215719" src="https://github.com/user-attachments/assets/9b373777-4c3d-4e02-aea0-9b0d668497d3" />

  - **Source and destination MAC addresses**

  
<img width="961" height="101" alt="Pasted image 20260603215657" src="https://github.com/user-attachments/assets/725ba157-5bad-4e67-88a1-015c7066c387" />


  - **Source and destination port numbers**
    
<img width="840" height="63" alt="Pasted image 20260603215819" src="https://github.com/user-attachments/assets/099daef9-f84e-4ba5-854c-c7147d4e42bb" />


- **Packet lengths**
      
<img width="340" height="25" alt="Pasted image 20260603220734" src="https://github.com/user-attachments/assets/335bffb6-d67d-4113-9b3c-26c4749e4dc8" />


### 4. Using Wireshark Display Filters

- Applied display filters to isolate specific protocols.
- Filtered and reviewed:

    - **DNS traffic**

    <img width="1351" height="149" alt="Pasted image 20260603230223" src="https://github.com/user-attachments/assets/1a95f1bb-aff4-42a7-9b9b-8ac05d015463" />


    - **TCP traffic**

   <img width="1340" height="178" alt="Pasted image 20260603230259" src="https://github.com/user-attachments/assets/55ee640d-e05e-41f8-a0ab-3e6d0b0af5c2" />


    - **HTTP traffic**

<img width="1344" height="173" alt="Pasted image 20260603230352" src="https://github.com/user-attachments/assets/4d1f699c-49e5-4787-ac6a-f0b573e4cfcd" />


### 5. Capturing Traffic with TCPdump

- **List all available network interfaces on the system**

```bash
┌──(kali㉿chayma)─[~]
└─$ tcpdump -D
```
Capture traffic on interface eth0 and display packet details in real-time

```bash
┌──(kali㉿chayma)─[~]
└─$ sudo tcpdump -i eth0
```
Capture traffic on eth0 and save it to a file named "capture.pcap" for further analysis

```bash
┌──(kali㉿chayma)─[~]
└─$ sudo tcpdump -i eth0 -w capture.pcap
```
Read and display packet details from a previously captured file "capture.pcap"

```bash
┌──(kali㉿chayma)─[~]
└─$ tcpdump -r capture.pcap
```
Capture packets originating from a specific source IP address

```bash
┌──(kali㉿chayma)─[~]
└─$ tcpdump src 192.168.1.4
```
Capture packets destined for a specific IP address

```bash
┌──(kali㉿chayma)─[~]
└─$ tcpdump dst 34.223.124.45
```
Capture packets with a specific port number, like port 80 (HTTP)

```bash
┌──(kali㉿chayma)─[~]
└─$ tcpdump port 80
```
Filter for packets that have the ACK flag

```bash
┌──(kali㉿chayma)─[~]
└─$ tcpdump -r traffic.pcap "tcp[tcpflags] & tcp-ack != 0"
```
