## Virtualization, Networking
## 1.Ping 8.8.8.8
<img width="556" height="380" alt="download" src="https://github.com/user-attachments/assets/57111161-4d32-4213-840a-bb0aa55cacb4" />


- **What does the ping command do?**  
  Sends ICMP Echo Request messages to a specified IP address and waits for Echo Replies, helping users verify if a device is reachable on the network, provide information about latency (response time) and packet loss.

- **What is the IP address 8.8.8.8, and why is it commonly used?**  
  8.8.8.8 is a public DNS server operated by Google. It is commonly used because:
  - It is highly reliable and always online. Google's servers are globally distributed. If one server goes down in a location, another responds immediately.
  - Fast Response.
  - It is often used for testing internet connectivity.

- **What is the objective of running this command?**  
  The objective is to check if your device has internet connectivity. It also measures network response time (latency) and helps diagnose network issues (if requests fail or time out).

## 2.1. Use the traceroute command from Kali

```bash
traceroute 8.8.8.8
```

<img width="605" height="182" alt="download" src="https://github.com/user-attachments/assets/afbb8b36-bb97-4daa-8cf2-2c3aaa707654" />


- **What does it show?**  
  It shows the network path (sequence of routers/hops) that data packets travel from my local device to Google's public DNS server.

- **How many hops does it take to reach Google's DNS?**  
  It takes 17 hops to reach Google's DNS server.

- **What does each line represent?**  
  Each numbered line represents a specific hop (a router) the packet passes through. Each line contains:
  - Hop number (1, 2, 3...)
  - Router IP address
  - Response time for that hop (latency)

## 3. Identify the IP address of your Kali Linux VM and your Windows host machine

- Use the appropriate command to find both IP addresses (e.g., `ip a` on Kali and `ipconfig` on Windows).

<img width="605" height="73" alt="download" src="https://github.com/user-attachments/assets/6d21fbd2-f95e-436e-baf1-63f0452fc8ea" />


**Kali IP Address:** `192.168.222.227`

<img width="611" height="144" alt="download" src="https://github.com/user-attachments/assets/591d0c47-f2b5-4e27-adb0-54f5b1805fe6" />


**Windows IP Address:** `192.168.222.12`

- **Try to ping one machine from the other**

<img width="602" height="195" alt="download" src="https://github.com/user-attachments/assets/9dde5f7c-88f7-4051-aa4d-2fc5968a502f" />

<img width="528" height="111" alt="download" src="https://github.com/user-attachments/assets/f0f4d67b-9ee9-4aac-96f8-aff60ec3c68c" />


- **Can they communicate? Explain the result.**  
  Yes, the machines have network connectivity, but the communication may appear one-way depending on firewall settings.

  Since I am using **Bridged mode**, both my host machine and the Kali VM appear as separate devices on the same local network. The Windows host can successfully reach and ping the Kali VM. However, the Kali VM cannot ping the Windows host by default because **Windows Defender Firewall blocks incoming ICMP (ping) requests**.

## 4. In VirtualBox network settings, test the following modes

- NAT
- Bridged Adapter

- **What is the difference between these two modes?**  

  - **NAT**:  
    In this mode, the virtual machine relies on the host to act as a NAT device. With NAT mode, a virtual DHCP server is responsible for assigning IP addressing information to these virtual machines, and they form a private network. Other machines on the physical network get IP addressing information from the physical DHCP server and form an external network. The host sits between these two networks and translates the IP address from a virtual machine to the IP address of the host. It also listens for returning traffic so that it can deliver it to the virtual machine. The external physical network sees traffic from the virtual machine as if it comes from the host itself.

  - **Bridged Adapter**:  
    In Bridged mode, a virtual machine connects directly to the physical network through the host's physical network interface (NIC). The host acts as a bridge between the virtual machines and the physical network. Virtual machines obtain IP addressing information from the DHCP server on the physical network. When using Bridged mode, a virtual machine appears to other devices on the network as just another physical computer, as if it were a separate machine connected directly to the network.

- **In which mode is the VM able to ping the host machine and vice versa?**  
  The VM is able to ping the host machine and vice versa on **Bridged Adapter** mode.

- **Explain your observations**  
  In **NAT mode**, the external physical network sees traffic from the virtual machine as if it originates from the host itself. Consequently, Kali can ping the host machine, but the host cannot reach Kali because the virtual machine is hidden behind a private virtual network.  
  When using **Bridged mode**, a virtual machine appears to other devices on the network as a separate physical computer connected directly to the network. Therefore, the Windows host can successfully reach and ping the Kali VM, and the Kali VM can also ping the Windows host (provided the Windows firewall is disabled to allow incoming traffic).

## 6. Launch XAMPP and access the default web page in your browser

- **What IP address is used to access the local web server?**  
  (Hint: Try accessing http://localhost or http://127.0.0.1)

  The IP address used to access the local web server is `http://localhost` or `http://127.0.0.1`.

## 7. Modify the default index.html file in the XAMPP htdocs folder

- Add your full name to the page.
- Open the page in your browser to verify the change.
- Take a screenshot and attach it.

<img width="605" height="148" alt="download" src="https://github.com/user-attachments/assets/e513c398-f466-4cf8-a378-4f995857c474" />


## 8. Try to access the XAMPP web server from Kali Linux

- **Were you able to reach the XAMPP page?**  
  Yes, I was able to reach the XAMPP page.

<img width="605" height="127" alt="download" src="https://github.com/user-attachments/assets/9b52643a-ec55-4a80-a185-88bb012715f6" />


- **If not, what configuration changes are needed (network mode, firewall, etc.)? Do some research and explain what should be done.**  
  - I used **Bridged network mode** in VirtualBox so that both Kali Linux and the Windows host are on the same local network and can communicate directly.  
  - Initially, Kali could not access the Apache server due to **Windows Firewall** blocking incoming traffic. I allowed Apache through Windows Firewall by creating a new inbound rule to allow connections to the Apache server on private networks.

<img width="605" height="243" alt="download" src="https://github.com/user-attachments/assets/cb7bb29b-203c-42a9-9b0c-a59d34319e4a" />

  - I also changed the **Network profile type** on Windows from **Public to Private**. Because the firewall rule explicitly specified **Private Only**, Windows would completely drop Kali's incoming traffic if the Wi-Fi connection remained classified as Public.

<img width="516" height="396" alt="download" src="https://github.com/user-attachments/assets/2b066521-9d29-4e60-a080-98d1ea1121fd" />


## 9. Use nmap from Kali Linux to scan the Windows host machine

```bash
nmap -sV <IP_of_Host>
```

<img width="605" height="241" alt="download" src="https://github.com/user-attachments/assets/6d2680fe-ea66-46f6-9314-c149907ba99a" />


- **What open ports are detected?**  
  Open ports: 80 (http), 135 (msrpc), 443 (ssl/http), 2179 (vmrdp?), 3306 (mysql), 5357 (wsdapi).

- **What is the version of the web server (Apache)?**  
  Apache httpd 2.4.54.

- **Can you identify the database server (e.g., MySQL) and its version?**  
  MariaDB 10.3.23.
```
