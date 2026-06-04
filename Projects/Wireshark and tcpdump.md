## Activities Performed

### 1. Capturing Network Traffic with Wireshark

- Opened Wireshark on a Kali Linux system.
- Selected the appropriate network interface (eth0).
- Generated network traffic by accessing   NeverSSL website through Firefox.
- Captured and analyzed packets in real time.
  
![[Pasted image 20260531195402.png]]
### 2. Analyzing the TCP Three-Way Handshake

- Identified the TCP connection establishment process.
- Observed:
    - SYN packet
    - SYN-ACK packet
    - ACK packet
    ![[Pasted image 20260603214143.png]]
- Verified successful TCP session establishment between client and server.

### 3. Examining Packet Details

- Analyzed packet information across Wireshark panes.
- Reviewed:
    - Source and destination IP addresses
    
     ![[Pasted image 20260603215719.png]]
       
    - Source and destination MAC addresses
     ![[Pasted image 20260603215657.png]]
       

    - Source and destination port numbers
     ![[Pasted image 20260603215819.png]]
    
    -
    - Packet lengths 

     ![[Pasted image 20260603220734.png]]
### 4. Using Wireshark Display Filters

- Applied display filters to isolate specific protocols.
- Filtered and reviewed:
    - DNS traffic
    ![[Pasted image 20260603230223.png]]
    - TCP traffic
    ![[Pasted image 20260603230259.png]]
    - HTTP traffic
    ![[Pasted image 20260603230352.png]]

### 5. Capturing Traffic with TCPdump


- List all available network interfaces on the system
  <div style="background-color: #0f1419; color: #00ff00; font-family: 'Courier New', monospace; padding: 15px; border-radius: 5px; border: 1px solid #1a233a; line-height: 1.5;">
<span style="color: #888888;">┌──(</span><span style="color: #ff5555; font-weight: bold;">kali㉿chayma</span><span style="color: #888888;">)─[</span><span style="color: #ffffff;">~</span><span style="color: #888888;">]</span><br>
<span style="color: #888888;">└─</span><span style="color: #00ffff; font-weight: 
bold;">$</span> tcpdump -D<br>
</div>

- Capture traffic on interface eth0 and display packet details in real-time.
<div style="background-color: #0f1419; color: #00ff00; font-family: 'Courier New', monospace; padding: 15px; border-radius: 5px; border: 1px solid #1a233a; line-height: 1.5;">
<span style="color: #888888;">┌──(</span><span style="color: #ff5555; font-weight: bold;">kali㉿chayma</span><span style="color: #888888;">)─[</span><span style="color: #ffffff;">~</span><span style="color: #888888;">]</span><br>
<span style="color: #888888;">└─</span><span style="color: #00ffff; font-weight: 
bold;">$</span> sudo tcpdump -i eth0<br>
</div>

- Capture traffic on eth0 and save it to a file named "capture.pcap" for further analysis
<div style="background-color: #0f1419; color: #00ff00; font-family: 'Courier New', monospace; padding: 15px; border-radius: 5px; border: 1px solid #1a233a; line-height: 1.5;">
<span style="color: #888888;">┌──(</span><span style="color: #ff5555; font-weight: bold;">kali㉿chayma</span><span style="color: #888888;">)─[</span><span style="color: #ffffff;">~</span><span style="color: #888888;">]</span><br>
<span style="color: #888888;">└─</span><span style="color: #00ffff; font-weight: 
bold;">$</span> sudo tcpdump -i eth0 -w capture.pcap<br>
</div>


- Read and display packet details from a previously captured file "capture.pcap"
<div style="background-color: #0f1419; color: #00ff00; font-family: 'Courier New', monospace; padding: 15px; border-radius: 5px; border: 1px solid #1a233a; line-height: 1.5;">
<span style="color: #888888;">┌──(</span><span style="color: #ff5555; font-weight: bold;">kali㉿chayma</span><span style="color: #888888;">)─[</span><span style="color: #ffffff;">~</span><span style="color: #888888;">]</span><br>
<span style="color: #888888;">└─</span><span style="color: #00ffff; font-weight: 
bold;">$</span> tcpdump -r capture.pcap<br>
</div>

- Capture packets originating from a specific source IP address
<div style="background-color: #0f1419; color: #00ff00; font-family: 'Courier New', monospace; padding: 15px; border-radius: 5px; border: 1px solid #1a233a; line-height: 1.5;">
<span style="color: #888888;">┌──(</span><span style="color: #ff5555; font-weight: bold;">kali㉿chayma</span><span style="color: #888888;">)─[</span><span style="color: #ffffff;">~</span><span style="color: #888888;">]</span><br>
<span style="color: #888888;">└─</span><span style="color: #00ffff; font-weight: 
bold;">$</span> tcpdump src 192.168.1.4<br>
</div>

- Capture packets destined for a specific IP address
<div style="background-color: #0f1419; color: #00ff00; font-family: 'Courier New', monospace; padding: 15px; border-radius: 5px; border: 1px solid #1a233a; line-height: 1.5;">
<span style="color: #888888;">┌──(</span><span style="color: #ff5555; font-weight: bold;">kali㉿chayma</span><span style="color: #888888;">)─[</span><span style="color: #ffffff;">~</span><span style="color: #888888;">]</span><br>
<span style="color: #888888;">└─</span><span style="color: #00ffff; font-weight: 
bold;">$</span> tcpdump dst 34.223.124.45<br>
</div>


- Capture packets with a specific port number, like port 80 (HTTP)
<div style="background-color: #0f1419; color: #00ff00; font-family: 'Courier New', monospace; padding: 15px; border-radius: 5px; border: 1px solid #1a233a; line-height: 1.5;">
<span style="color: #888888;">┌──(</span><span style="color: #ff5555; font-weight: bold;">kali㉿chayma</span><span style="color: #888888;">)─[</span><span style="color: #ffffff;">~</span><span style="color: #888888;">]</span><br>
<span style="color: #888888;">└─</span><span style="color: #00ffff; font-weight: 
bold;">$</span> tcpdump port 80<br>
</div>

- Filter for packets that have the **ACK** flag
<div style="background-color: #0f1419; color: #00ff00; font-family: 'Courier New', monospace; padding: 15px; border-radius: 5px; border: 1px solid #1a233a; line-height: 1.5;">
<span style="color: #888888;">┌──(</span><span style="color: #ff5555; font-weight: bold;">kali㉿chayma</span><span style="color: #888888;">)─[</span><span style="color: #ffffff;">~</span><span style="color: #888888;">]</span><br>
<span style="color: #888888;">└─</span><span style="color: #00ffff; font-weight: 
bold;">$</span> tcpdump -r traffic.pcap "tcp[tcpflags] & tcp-ack != 0"
<br>
</div>
## Skills Developed

- Network traffic capture
- Packet analysis
- Wireshark filtering
- TCPdump usage
- Protocol analysis
