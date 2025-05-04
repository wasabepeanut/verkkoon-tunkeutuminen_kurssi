# a) Evilginx2
For this task I will install the tool Evilginx following the [instructions](https://help.evilginx.com/pro/installation/local).

To make Evilginx work we will first need to install the tools Golang and nvm.

**Golang**

        rm -rf /usr/local/go && tar -C /usr/local -xzf go1.24.2.linux-amd64.tar.gz


**nvm**

    curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash

After installation, I restarted terminal and checked if I have nvm installed now.

    nvm --version

![image](https://github.com/user-attachments/assets/004e50ac-3ad1-4b78-b95e-a049b9f43a73)

Now we can proceed to installing node.js.

**node.js**

    nvm install 18

![image](https://github.com/user-attachments/assets/336b06af-6bae-4076-a236-459cb8f8feb9)

    nvm use 18
    
![image](https://github.com/user-attachments/assets/af09ef48-eff2-46fc-92e3-ee4e1af97b86)

Checking to see that we have node.js with the right version

    node -v

![image](https://github.com/user-attachments/assets/4b0c4b3c-e61d-49eb-b0cc-4e6a6c68509a)



# Mininet
To complete the upcoming tasks, I will have to install Mininet VM.

I followed the instructions on the [official Mininet website](https://mininet.org/download/#option-1-mininet-vm-installation-easy-recommended).

First I downloaded the [VM Image](https://github.com/mininet/mininet/releases/download/2.3.0/mininet-2.3.0-210211-ubuntu-20.04.1-legacy-server-amd64-ovf.zip).

Secondly I had to download a virtualization system. As I already had Oracle Virtualbox, I skipped this part.

After my VM Image was downloaded, I extracted the content and then double-clicked on the ovf file. This took me straight to Oracle VirtualBox and after that I imported the file with default settings.

![image](https://github.com/user-attachments/assets/716e28fb-aac3-4e55-87ea-c64a9d37b6a5)

Now I have installed a Mininet VM. I will test to see if it works.

![image](https://github.com/user-attachments/assets/d39ff571-981b-4730-a278-584718591009)

Seems to work fine.


# References

Evilginx. 2025. Getting Started. URL: https://help.evilginx.com/community/getting-started. Accessed: 4.5.2025.

kgretzky. 21.1.2025. evilginx2. GitHub. URL: https://github.com/kgretzky/evilginx2. Accessed: 4.5.2025.

Mininet. 2022. Download/Get Started With Mininet. URL: https://mininet.org/download/#option-1-mininet-vm-installation-easy-recommended. Accessed: 4.5.2025.

