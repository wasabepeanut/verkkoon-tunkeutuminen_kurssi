# a) Tutustu wifi challenge lab 2.1 harjoitus ympäristöön ja käytä tarvittaessa hyväksesi jo olemassa olevia ohjeita

In this exercise I will be familiarizing myself with the Wifi Challenge Lab 2.1. 


## Prerequisites

For starters, I went to the [WifiChallenge website](https://lab.wifichallenge.com/) and created an account for myself.

After logging in, I went to the README tab.

![image](https://github.com/user-attachments/assets/d6b0ab6a-aaa4-44ed-b87a-c970d8001333)

I proceeded to download the folder for VirtualBox from the [Proton Drive link](https://drive.proton.me/urls/Q4WPB23W7R#Qk4nxMH8Q4oQ) (since I am using VBox).

Content of the VirtualBox folder:

![image](https://github.com/user-attachments/assets/c6eafe0c-f95a-4f7f-8538-3267a7fde902)

I double clicked the ".ova" file in the folder and imported the file to VirtualBox with default settings.

![image](https://github.com/user-attachments/assets/5957ff03-69cd-46df-88c1-6c72c9861578)

Then I launched the VM.

![image](https://github.com/user-attachments/assets/3f65deb1-f578-47c8-a293-6bf53f26bb3c)

Logging in user

![image](https://github.com/user-attachments/assets/fc6898e0-a042-4554-8e5e-d3d05aaeed86)

We are in!
Now also before I start doing any challenges, I changed the keyboard layout to Finnish by committing this command in the terminal.

    setxkbmap fi

## Challenges
### 00. What is the contents of the file /root/flag.txt on the VM?

I simply executed the command:

    sudo cat /root/flag.txt

![image](https://github.com/user-attachments/assets/9ddd849a-96f5-410b-a5c8-dcb5cfacf90d)

**Flag:** flag{2162ae75cdefc5f731dfed4efa8b92743d1fb556}


### 01. What is the channel that the wifi-global Access Point is currently using?

First I tried committing the command:

    sudo airodump-ng wlan0

![image](https://github.com/user-attachments/assets/abfc8bea-def2-44e0-8e08-c2e4682daac3)

This gave me a lot of entries, but not the "wifi-global". I tried using grep with the same command.

    sudo airodump-ng wlan0 | grep wifi-global

This did not work.
I decided to use the walkthrough for help :).

Creating a new directory to store all the captures.

    mkdir ~/wifi
    sudo airmon-ng start wlan0

![image](https://github.com/user-attachments/assets/7077309b-1442-4f0d-b6e5-0bfa56582131)

I got some kind of a warning. I ran the recommended command:

    sudo airmon-ng check kill

![image](https://github.com/user-attachments/assets/0838edcc-da0d-4a10-8422-c5b2bdc82aff)

Starting wlan0 again.

    sudo airmon-ng start wlan0
    sudo airodump-ng wlan0mon -w ~/wifi/scan --manufacturer --wps --band abg

![image](https://github.com/user-attachments/assets/5dbe42ae-88e6-45ab-8e27-5b7c1f7e7e5b)

**Flag:** 44

### 02. What is the MAC of the wifi-IT client?

Since we know the channel of "wifi-IT" from the previous task' screenshot, we can only scan the specific channel:

    sudo airodump-ng wlan0mon -w ~/wifi/scan11 --manufacturer --wps -c11

**Flag:** "10:F9:6F:AC:53:52"

### 03. What is the probe of 78:C1:A7:BF:72:46?
### 04. What is the ESSID of the hidden AP (mac F0:9F:C2:6A:88:26)?
### 06. What is the flag on the AP router of the wifi-guest network?
### 07. What is the flag on the wifi-old AP website?

# b) Kirjoita raportti siitä mitä opit ja mitkä asia yllättivät sinut kun tutustuit harjoitukseen.



# c) Miten suhtautumisesi WLanin turvallisuuteen muuttui sen jälkeen kun teit harjoitukset?


# References

r4ulcl. 21.12.2024. WiFiChallenge Lab. URL: https://lab.wifichallenge.com/README. Accessed: 14.5.2025.
