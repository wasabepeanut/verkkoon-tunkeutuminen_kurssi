# x) Wireshark
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

# b) Can't fish
To prove that I can disable and/or enable my virtualbox' internet connection.

Disabling:
I clicked the network icon from the top right and chose "disconnect".

![image](https://github.com/user-attachments/assets/82e6de62-86c9-4473-bf2c-38aa528ddccc)

![image](https://github.com/user-attachments/assets/5501e856-9042-4f49-9d57-0265ff0a30d3)


Enabling:
I clicked the same icon and chose the available network.

![image](https://github.com/user-attachments/assets/0636fc5b-892e-42a3-bbdc-528eae649aa2)

![image](https://github.com/user-attachments/assets/9abb91ab-7e81-4095-836b-ce8150d384ec)


# References

Karvinen, T. 22.1.2021. Install Debian on Virtualbox - Updated 2024. TeroKarvinen. URL: https://terokarvinen.com/2021/install-debian-on-virtualbox/. Accessed: 1.4.2025.

Karvinen, T. 28.3.2025. Network Interface Names on Linux. TeroKarvinen. URL: https://terokarvinen.com/network-interface-linux/. Accessed: 1.4.2025.

Karvinen, T. 28.3.2025. Wireshark - Getting Started. TeroKarvinen. URL: https://terokarvinen.com/wireshark-getting-started/. Accessed: 1.4.2025.

PagerDuty. 2025. Network Sniffers: What Are They and How Can I Use Them?. URL: https://www.pagerduty.com/resources/monitoring/learn/what-are-network-sniffers/. Accessed: 1.4.2025.
