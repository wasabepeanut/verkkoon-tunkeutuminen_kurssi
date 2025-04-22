# 1) Tarkastele käytössäsi olevia RFID tuotteita, mieti miten hyvin olet suojautunut RFID urkinnalta?
Some products/items that make use of RFID that I own are e.g. passport, HSL transportation card, library card and smartphone (Wikipedia 25.2.2025), that mostly work with NFC which is a form of RFID technology (Di Leo 27.11.2023).

When we think about the overall safety of these products, they are not that well protected since they are easily scannable and exploitable if you manage to get your hands on one. Although they are easily exploitable, the information you might get from exploiting them might not be as expected or useful.

Out of these items, smartphone would be the most valuable since it has a payment tool that uses NFC technology. An exploiter could get access to my payment card information by cloning it or physically stealing my phone. Both of these methods or pretty hard to execute in real life, since cloning requires the victim to use the phone very close to the cloning device for the NFC technology to be exploited (Stokes 24.2.2023). 

Overall I think the safety of my RFID products are not that secured (excluding my phone) since they do not have any actual security measures such as passwords. 


# 2) Tutustu APDU komentojen rakenteeseen (voit käyttää tekoälyä tutustumiseen)
An APDU commands are formed by hex byte sequences with variable lengths that are structured into distinct components (in order) CLA, INS, P1, P2 and other optional components (Olosunde 4.4.2023). For example an APDU command could look like "00 A4 04 00 07 D2 76 00 00 85 01 01".

Explanation of the components:
- CLA (Class byte) = Specifies the type of command being sent. In our example command it is "00", which is the default CLA.
- INS (Instruction byte) = Specifies the specific command being sent. In our example it is "A4" which corresponds to "Select File" command.
- P1 (Parameter 1 byte) = Additional information about the command. In our example it is "04" which indicates that the data field contains the Application Identifier (AID)
- P2 (Parameter 2 byte) = Same as P1. In our example it is "00".
- Data field: "07 D2 76 00 00 85 01 01" is the hex value of our AID, where the "07" indicates that the AID is 7 bytes long. (Olosunde 4.4.2023)

So to form a APDU command, we must atleast have a value with the 4 mandatory components, which will be set to "00" by default if a custom value is not present.


# 3) Tutki ja kerro minkä mielenkiintoisen RFID hakkerointi uutiset löysit. (Vinkki, useimmat liittyvät henkilökortteihin)
I found a [news topic](https://thehackernews.com/2018/04/hacking-hotel-master-key.html) that was about hackers who built a "Master Key" for various hotel rooms.

- Two researchers from F-Secure, Tomi Tuominen and Timo Hirvonen, managed to build a master key by exploiting a vulnerability in a popular electronic lock system. 
- The requirement for this "master key" was to first get a hold of an electronic keycard for any room and then by using their custom made software, they succeeded in creating the key.
- This master key would work by holding it near the target lock, which would then try different keys in a short time and result in the door being unlocked.
- This key would work in any hotel room using the same digital lock technology, without leaving a trace. (Khandelwal 26.4.2018)


# References

Di Leo, C. 27.11.2023. RFID & NFC: Which one is better access control system?. Spotter Security. URL: https://www.spottersecurity.com/blog/rfid-and-nfc-access-control/. Accessed: 22.4.2025.

Khandelwal, S. 26.4.2018. Hackers build a 'Master Key' that unlocks millions of Hotel rooms. The Hacker News. URL: https://thehackernews.com/2018/04/hacking-hotel-master-key.html Accessed: 22.4.2025.

Olosunde, A. 4.4.2023. Understanding APDU for Software Developers.. Medium. URL: https://medium.com/@lovisgod/understanding-apdu-for-software-developers-b82c17cc890a. Accessed: 22.4.2025.

Stokes, H. 24.2.2023. RFID Cloning – What is It & How It Works. Safe and Sound Security. URL: https://getsafeandsound.com/blog/rfid-cloning/. Accessed: 22.4.2025.

Wikipedia. 25.2.2025. RFID. URL: https://fi.wikipedia.org/wiki/RFID. Accessed: 22.4.2025.
