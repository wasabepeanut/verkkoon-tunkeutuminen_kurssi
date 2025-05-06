# a) Evilginx
## Installation

For this task I will install the tool Evilginx following the [instructions](https://help.evilginx.com/pro/installation/local).

To make Evilginx work we will first need to install the tools Golang and nvm.

**Golang**

First I downloaded the [file](https://go.dev/dl/).

    rm -rf /usr/local/go && tar -C /usr/local -xzf go1.24.2.linux-amd64.tar.gz

Adding /usr/local/go/bin to the PATH environment variable.

    export PATH=$PATH:/usr/local/go/bin

And lastly checking to see if the system has Golang now

    go version

![image](https://github.com/user-attachments/assets/976d7ee4-557d-4192-8186-36bf70eb05ee)

Building the Evilginx binary with the "make" command.

    make

![image](https://github.com/user-attachments/assets/13b190da-8f93-4f93-ac8c-97a59da54368)

At first it did not seem to work. I tried asking ChatGPT for assistance and according to it, I have to first be in the Evilginx project directory before giving the command.

With ChatGPT I also cloned the evilginx github repository to my home directory and committed the make command.

    git clone https://github.com/kgretzky/evilginx2.git
    cd evilginx2
    make

This seemed to work. According to the instructions, the built binary should be under build/.
This is what I found in the folder

![image](https://github.com/user-attachments/assets/ae381da8-393e-4048-8f5b-a168c490d8f5)

After building evilginx, I proceeded to run the tool normally:

    sudo ./build/evilginx

![image](https://github.com/user-attachments/assets/7b55d774-af6a-4b8d-9312-42311749f325)


## In action

Now I will proceed to simulate an phishing attack with the tool following the steps from a [guide](https://nateahess.medium.com/evilginx-quickstart-guide-b4124e8dc8f3).

First I will install [phislets](https://github.com/An0nUD4Y/Evilginx2-Phishlets), which are small config files used to configure Evilginx for attacks (Nate 6.12.2024).

    git clone https://github.com/An0nUD4Y/Evilginx2-Phishlets

Moving the phislets to the right directory:

    cp -r Evilginx2-Phislets/* /home/duyp/evilginx/phislets/

Checking the contents:

    ls -l /home/duyp/evilginx/phislets/

![image](https://github.com/user-attachments/assets/e736595a-2175-4a5a-8617-5503a529251c)

Seems right.
Now that I have the phislets, I can run the tool again with the phislets

    sudo ./build/evilginx -p ./phislets/

![image](https://github.com/user-attachments/assets/f6c44f3e-4a72-4cb4-b1f7-1b5ffcb97fa6)

![image](https://github.com/user-attachments/assets/5dc56743-5024-4d39-a7cf-bd64cd07366c)

This is what the output looked like.
I noticed that some links could be clicked so I tried following the link "www.amazon.com".

![image](https://github.com/user-attachments/assets/f4685ac4-ef40-49e8-95f3-f869ea7a024a)

This took me to Amazon (pretty obvious from the name).
This site is the official website for Amazon, except it has been "tampered" with Evilginx. Evilginx acts as a "Adversary in the Middle" that serves as a legitimate page for malicious acts (Nichols 8.14.2024).

Now I will try to configure a fake domain for phishing.

First I created a HTML file.

![image](https://github.com/user-attachments/assets/0a1840da-81f5-42af-b661-0f142cba567f)



# Mininet

I followed the instructions on the [official Mininet website](https://mininet.org/download/#option-1-mininet-vm-installation-easy-recommended) to install Mininet on Oracle Virtualbox.

First I downloaded the [VM Image](https://github.com/mininet/mininet/releases/download/2.3.0/mininet-2.3.0-210211-ubuntu-20.04.1-legacy-server-amd64-ovf.zip).

Secondly I had to download a virtualization system. As I already had Oracle Virtualbox, I skipped this part.

After my VM Image was downloaded, I extracted the content and then double-clicked on the ovf file. This took me straight to Oracle VirtualBox and after that I imported the file with default settings.

![image](https://github.com/user-attachments/assets/716e28fb-aac3-4e55-87ea-c64a9d37b6a5)

Now I have installed a Mininet VM. I will test to see if it works.

![image](https://github.com/user-attachments/assets/d39ff571-981b-4730-a278-584718591009)

Seems to work fine.


# References

Evilginx. 2025. Getting Started. URL: https://help.evilginx.com/category/getting-started. Accessed: 4.5.2025.

kgretzky. 21.1.2025. evilginx2. GitHub. URL: https://github.com/kgretzky/evilginx2. Accessed: 4.5.2025.

Mininet. 2022. Download/Get Started With Mininet. URL: https://mininet.org/download/#option-1-mininet-vm-installation-easy-recommended. Accessed: 4.5.2025.

Nate. 6.12.2024. Evilginx Quick-start Guide. Medium. URL: https://nateahess.medium.com/evilginx-quickstart-guide-b4124e8dc8f3. Accessed: 7.5.2025.

Nichols, B. 8.14.2024. Catching the Phish – Detecting Evilginx & AiTM. deepwatch. URL: https://www.deepwatch.com/labs/catching-the-phish-detecting-evilginx-aitm/. Accessed: 7.5.2025.
