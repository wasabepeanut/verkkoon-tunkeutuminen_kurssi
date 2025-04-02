# x) Wireshark 🦈
- One of the most popular tools used for network "sniffing" and analyzing (Karvinen 28.3.2025).
- Sniffing = monitoring network traffic for information (source, destination, protocols, etc.) (PagerDuty 2025).
- How to use:
  - Install the tool to your OS, such as Debian
  - Add the group of people to allow sniffing, and then update by logging back in
  - Choose the target network interfaces for sniffing. (Karvinen 28.3.2025)


# x) Network Interface Names
- Network interface = a "network card", but not necessarily physical.
- Interface types are determined by the start of the name called a "prefix".
- Prefix examples:
  - en = Wired Ethernet
  - wl = WLAN, WiFi
  - lo = Loopback adapter.
- Numbers after a prefix identify the device or the location where the computer is connected to. (Karvinen 28.3.2025) 


# a) Installing Debian
I followed the instructions and installed Debian on my Linux virtualbox without problems. (Karvinen 22.1.2021)

![image](https://github.com/user-attachments/assets/fdb09b0c-1f23-43e1-8c46-0fe8f1b73bde)

# b) Can't fish 🎣
To prove that I can disable and/or enable my virtualbox' internet connection.

Disabling:
I clicked the network icon from the top right and chose "disconnect".

![image](https://github.com/user-attachments/assets/82e6de62-86c9-4473-bf2c-38aa528ddccc)

![image](https://github.com/user-attachments/assets/5501e856-9042-4f49-9d57-0265ff0a30d3)


Enabling:
I clicked the same icon and chose the available network.

![image](https://github.com/user-attachments/assets/0636fc5b-892e-42a3-bbdc-528eae649aa2)

![image](https://github.com/user-attachments/assets/9abb91ab-7e81-4095-836b-ce8150d384ec)


# c) Installing Wireshark 
I followed the lecturer's instructions for installing Wireshark on Debian. (Karvinen 28.3.2025)

First I opened the terminal, got the latest updates and started the installation with:

    sudo apt-get update
    sudo apt-get install wireshark

![image](https://github.com/user-attachments/assets/b1fa3106-9730-4881-8694-39201fb2e6bf)

Continued with "yes" and now my OS should have Wireshark.
After that I added my user (duyp) to wireshark and then relogged in.

    sudo adduser duyp wireshark

![image](https://github.com/user-attachments/assets/f3941bc7-69c2-4461-8f34-d3992d355e8c)

Then I opened the interface with "wireshark" command and chose "enp0s3" as my target:

    wireshark

![image](https://github.com/user-attachments/assets/5bcfa315-11ae-40cb-865e-7b0d86991795)

As we can see from the screenshot, we are now sniffing.


# d) TCP/IP
For this exercise I chose to capture a packet with HTTP protocol, so that it contains all four layers of TCP/IP model.

![image](https://github.com/user-attachments/assets/bc7574c1-5fc3-490b-b031-c77ad95b5bf2)

As we can see in the screenshot, this packet has all four layers:
- Datalink layer:
  - **Ethernet II**
  - Handles the physical act of sending and receiving data between applications or devices on a network (Fortinet 2025).
  
- Internet layer:
  - **Internet Protocol Version 4 (IPv4)**
  - Sends and controls packets from a network while ensuring its safe arrival (Fortinet 2025).
 
- Transport layer:
  - **Transmission Control Protocol (TCP)**
  - Provides reliable data connection between the source and destination (Fortinet 2025).
    
- Application layer:
  - **Hypertext Transfer Protocol (HTTP)**
  - The user friendly part of the model, refers to programs that need TCP/IP for communication (Fortinet 2025).

# e) Surfing 🏄‍♂️
For this exercise I will be analyzing and explaining what kind of a capture the [surfing-secure.pcap](https://terokarvinen.com/verkkoon-tunkeutuminen-ja-tiedustelu/surfing-secure.pcap)
file is.

At first we can see from the bottom bar that the capture contains a total of 283 packets.

![image](https://github.com/user-attachments/assets/2107429a-833c-4abd-a6dc-8edd712ea7c6)

We can also determine the duration of this capture by looking at the time of the last capture, which was about 7.5 seconds.

![image](https://github.com/user-attachments/assets/9cfcf781-0dc0-4aef-b976-b23959d45f22)

The protocols that appear often in this capture are DNS, QUIC, TCP and TLS.
Judging by the number of TLS and QUIC protocols, this capture seems to be of secured web surfing, since TLS (Transport Layer Security) is used for encryption of the communication between web applications (Cloudflare 2025). As for QUIC (Quick UDP Internet Connections), it is mainly used for efficient and fast communication, as the name implies (Haproxy 25.10.2024).

Then I proceeded to "File Properties" from "Statistics" on the navigation bar. There we could e.g. see the actual date of when this capture was made.

![image](https://github.com/user-attachments/assets/6d9075fa-78ed-4fe7-aea3-a8acb6f7bdde)

![image](https://github.com/user-attachments/assets/d38c80d5-07ca-409e-9fdd-934815ba1a83)

From the same Statistics button I proceeded to "Conversations" where I could see the different communications between the source and destinations. There was a total of 6 different communications on IPv4.

![image](https://github.com/user-attachments/assets/dbaa95d3-3804-420e-a8b6-3e992bff9663)


# g) Network Card
In this task we have to determine the network card of the user in the same file mentioned in the previous task.

Wireshark seems to find this automatically from the source as we can see in the screenshot below:

![image](https://github.com/user-attachments/assets/4521deb8-b296-4689-8893-ca0681dcad76)

The brand of the network card is RealtekU. 


# h) Web server
For this task we have to find out the web servers where the user has been surfing.
By looking around for a while, I found out from the DNS packets that the user has atleast been surfing on google.com, terokarvinen.com and terokarvinen.goatcounter.com.

![image](https://github.com/user-attachments/assets/206a3240-50f2-44fb-87ca-c95fe941930f)

![image](https://github.com/user-attachments/assets/d03ea79d-6bbc-49a2-b6c7-c177f70b020f)

# i) My capture
In this task I will be analyzing my own capture and explaining what is going on. 
For starters I chose enp0s3 as my target, and opened Mozilla Firefox.

![image](https://github.com/user-attachments/assets/3901cd53-5efd-4f7c-8c28-ff5d786d32cd)

As we can see in the picture, the first thing happening is a DNS request from the source (me). This happened when I opened the browser, so in a nutshell I am requesting communication from the web browser Mozilla Firefox. It takes about 0.03 seconds for me to get a response from the web browser. 

![image](https://github.com/user-attachments/assets/9f6e8ddf-412e-4073-8ddd-45a4c0570428)

In details when I am making the request I am first "creating" my request which my device will then form into a packet. The packet will then go through the layers of TCP/IP model and proceed securely to the destination, in this case the destination IP is 10.0.2.3. When the packet is securely delivered, the receiver will then process my request and do the same for their response. The response packet will then be forwarded to the original (source), in this case 10.0.2.15. This is a what happens between a communication of two devices.


# References 📖

Cloudflare. 2025. What is TLS (Transport Layer Security)?. URL: https://www.cloudflare.com/learning/ssl/transport-layer-security-tls/. Accessed: 2.4.2025.

Fortinet. 2025. What is Transmission Control Protocol TCP/IP?. URL: https://www.fortinet.com/resources/cyberglossary/tcp-ip. Accessed: 2.4.2025.

Haproxy. 25.10.2024. What is QUIC?. URL: https://www.haproxy.com/glossary/what-is-quic. Accessed: 2.4.2025.

Karvinen, T. 22.1.2021. Install Debian on Virtualbox - Updated 2024. TeroKarvinen. URL: https://terokarvinen.com/2021/install-debian-on-virtualbox/. Accessed: 1.4.2025.

Karvinen, T. 28.3.2025. Network Interface Names on Linux. TeroKarvinen. URL: https://terokarvinen.com/network-interface-linux/. Accessed: 1.4.2025.

Karvinen, T. 28.3.2025. Wireshark - Getting Started. TeroKarvinen. URL: https://terokarvinen.com/wireshark-getting-started/. Accessed: 1.4.2025.

PagerDuty. 2025. Network Sniffers: What Are They and How Can I Use Them?. URL: https://www.pagerduty.com/resources/monitoring/learn/what-are-network-sniffers/. Accessed: 1.4.2025.
