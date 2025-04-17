# x) Universal Radio Hacker

- Hacking 433 mHz devices with On-Off Key (OOK) modulation scheme.
- To start hacking, you will first need to install Universal Radio Hacker (URH) and Toolchain.
- In a nutshell, you can hack a device by copying the signal and sending it from another device. (hubmartin 18.1.2019)


# x) Decode 433.92 MHz weather station data

- rtl_433, a powerful utility used for receiving and decodings signals.
- Universal Radio Hacker (URH), a software tool that can be used for recording, analyzing, tweaking and re-transmitting signals.
- Workflow of the decoding process:
  - Capturing transmission: Setting up the corresponding information for the analyzer and recording the wanted signal.
  - Demodulation: Checking and identifying the captured signal and detecting with autodetect and the right settings.
  - Analysis: Analyzing our results and taking notes. (Cornelius 4.1.2022)

 
# a) WebSDR

For this task I used [NA5B WebSDR](http://na5b.com:8901/) which operates in the U.S, Washington DC Area.

When I first opened the page, I could already hear some narrating from some radio. I then started to play around a little, clicking and testing what and how the buttons would change the sound.

Information of the audio:
- Frequency: ~730 Hz
- Bandwidth: MW-160
- Modulation: AM

After playing around a little, I could determine that most of the signals work on the AM mode. Changing the mode from AM to anything else on most cases altered the sounds or made it unrecognizable.

![image](https://github.com/user-attachments/assets/d8eeb8f6-9c2e-49a6-a44a-e6cd7193cb6e)

As we can see from the picture, the sizes of the signals being send were different. I zoomed in the waterfall and tuned the size of the "receiver" to match the size of the signal, atleast as much as possible. This could be done by manually resizing the yellow receiver or from the Filter option.

![image](https://github.com/user-attachments/assets/5e2cf7c3-a3f1-42d5-8510-09d6d8156534)

![image](https://github.com/user-attachments/assets/a5a1abe3-52af-4c79-882e-8b371a57e38d)

This clearly made the sound way better and have less background noises.
It also in most cases was better for the size of the receiver to be a bit wider than the signal. This was true for atleast the smaller sized signals. 
Narrowing the receiver did although reduce the background noises more. 


# b) rtl_433

For this task I will be installing rtl_433 for automatic analyzation.

    sudo apt-get update
    sudo apt-get install rtl-433

And after installation, I tried to run rtl_433

    rtl_433 -h

![image](https://github.com/user-attachments/assets/0f9ec8be-8910-42e4-a7ba-0fe72b02d29d)
    
![image](https://github.com/user-attachments/assets/47307a63-c4c9-41ad-a069-ddeb359b486f)

Installation seemed to work. (merbanan 19.2.2025)


# c) Automatic analyzation

For this task I will be using the previously installed rtl_433 to analyze a [file](https://terokarvinen.com/verkkoon-tunkeutuminen-ja-tiedustelu/samples/Converted_433.92M_2000k.cs8). (Karvinen 26.3.2025)

    rtl_433 -r Converted_433.92M_2000k.cs8

The "-r" parameter in this command is to notify that we will be executing rtl_433 on a file. The "M" in the file name is for frequency and the "k" is for sample rate (merbanan 19.2.2025).

![image](https://github.com/user-attachments/assets/c90bc963-f106-4a5e-8c96-ac131ea4c5f4)

![image](https://github.com/user-attachments/assets/63bdc1ad-0a57-4026-912c-6cb1b46b0450)



# References

Cornelius. 4.1.2022. Decode 433.92 MHz weather station data. One Transistor. URL: https://www.onetransistor.eu/2022/01/decode-433mhz-ask-signal.html. Accessed: 17.4.2025.

hubmartin. 18.1.2019. Universal Radio Hacker SDR Tutorial on 433 MHz radio plugs. Youtube. URL: https://www.youtube.com/watch?v=sbqMqb6FVMY&t=199s. Accessed: 16.4.2025.

Karvinen, T. 26.3.2025. Verkkoon tunkeutuminen ja tiedustelu. Tero Karvinen. URL: https://terokarvinen.com/verkkoon-tunkeutuminen-ja-tiedustelu/. Accessed: 17.4.2025.

merbanan. 19.2.2025. rtl_433. GitHub. URL: https://github.com/merbanan/rtl_433. Accessed: 17.4.2025.

