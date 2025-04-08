# x) Pyramid of Pain 
The Pyramid of Pain is a visual model of seven layers of indicators used to detect adversary activity. 
The layers describe the amount of "pain" caused to the adversary, the bottom of the pyramid being the least painful and the pinnacle of the pyramid the most painful. (DavidJBianco 17.1.2014)


# x) Diamond Model 💎
Diamond model is a visual model that represent four core features, each forming an edge of a diamond (thus the name), that illustrate the fundamental relationships between the features. 
The model is used to analyze and enhance understanding of malicious activity. (Caltagirone 7.2013)


# a) Apache log
To start this task I will first proceed to install Apache for my virtualbox.

    sudo apt-get update
    sudo apt-get install apache2

Then I proceeded to my public default browser by typing "localhost" on Firefox.

![image](https://github.com/user-attachments/assets/4fdfb7d6-7c98-4f1d-ac2b-66e0657848f7)

Apache works!

Now to analyze my logs regarding my request to access this site, I printed the output of the access.log file in the path /var/log/apache2/access.log (hector adam 11.3.2016).

    sudo cat /var/log/apache2/access.log

![image](https://github.com/user-attachments/assets/c5d7112c-f248-4e46-8d47-3e95c858e1cd)

As we can see from the picture there are 3 log entries in the file. The first log ' "GET / HTTP/1.1" 200 3380... ' indicates that first we are making a GET request from resource / (root) with protocol version HTTP/1.1.
Then we have numbers 200 and 3380. 200 is a status code which means that the request is succesful. The latter is the size of the response in bytes (MDN web docs 14.3.2025).

The second log ' "GET /icons/openlogo-75.png" is almost the same but now we are retrieving data from another resource. The file is a "png" file, which usually tells us that the data is an image.

The last log is an "favicon" GET request which are used for the small "logos" on browser tabs. The status code 404 indicates that there was an error retrieving this data (MDN web docs 14.3.2025).


# b) Nmapped
For this task, I first disconnected my network on the virtualbox for safety measures and then gave the command:

    sudo nmap -A localhost
(Karvinen 26.3.2025).

Then I looked for the port 80/tcp.

![image](https://github.com/user-attachments/assets/47c9c4d7-ea88-412c-9d8a-c041fe062608)

From the output, we can see that the port is open under the "STATE", the service is HTTP and the server version is Apache.
From the portscan we can tell that the Apache is working fine and the website should also be visible for us.


# c) Scripts
The scripts that were automatically on using the parameter -A were:

![image](https://github.com/user-attachments/assets/c9ae8308-1be4-4ee6-8f16-1210f0d604ef)

The scripts usage can be determined from their names.


# d) Log traces
First I used the previously used command to check the access.log file.

    sudo cat /var/log/apache2/access.log

![image](https://github.com/user-attachments/assets/0d3f3d1d-e77b-4156-a476-7444327ad87a)

As we can see from the picture, the word nmap can be seen in the logs. Analyzing the the text "Nmap Scripting Engine" we can guess that these requests are from the scripts earlier, which might also explain why the requests sizes are not that big.
By using 'grep "nmap"' for example it is possible to find all log entries including the text "nmap" from the log file.


# e) Wire Sharking
First I launched Wireshark with the command:

    wireshark

Then I chose Loopback as my target and then started sniffing.
On another terminal, I executed portscan with only port 80/tcp and then filtered the wireshark to only show entries with nmap.

    sudo nmap -T4 -vv -A -p 80 localhost
(Karvinen 26.3.2025).

(On wireshark):

    frame contains "nmap"

![image](https://github.com/user-attachments/assets/8d69915b-d306-4f84-866e-bafa8e407dfa)

This whole portscan contained a total of 354 packets and it only took about 8 seconds.


# f) Net grep
For this task I first installed ngrep with:

    sudo apt-get update
    sudo apt-get install ngrep

Then I executed the command (Karvinen 26.3.2025):

    sudo ngrep -d lo -i nmap
(Karvinen 26.3.2025).
Now I should be capturing traffic with ngrep. After that I executed the portscan.

![image](https://github.com/user-attachments/assets/a13debbe-56f3-4a07-b67d-07b354bad7d1)


# g) Agent 🕵️‍♂️
I changed the useragent with the command:

    sudo nmap -p 80 --script-args http.useragent="Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/58.0.3029.110 Safari/537.3" -A 127.0.0.1

This changes every requests using http.useragent to blend a little bit better with the other entries. (bob van der staak. 17.11.2023)
I then proceeded using Wireshark to see how it is displayed there. I filtered only packets containing keyword "User-Agent"

![image](https://github.com/user-attachments/assets/9ebf9a32-8a17-4080-a7f0-4cbcffc114f2)

As we can see, it seems like a legit browser.

# h) Smaller traces
For this task I first executed a new portscan and then printed the output of the access-log file and also captured the traffic with ngrep.

    sudo nmap -p 80 --script-args http.useragent="Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/58.0.3029.110 Safari/537.3" -A 127.0.0.1
    sudo cat /var/log/apache2/access.log
    sudo ngrep -d lo -i nmap
    
    
Output of access.log:
![image](https://github.com/user-attachments/assets/a8de516f-8a07-4d38-b4a8-bcbf7ce40714)

Output of ngrep capture:
![image](https://github.com/user-attachments/assets/02455b98-6890-4412-b77e-2b6e338f275b)


As we can see in the image, the "nmap" logs appear with the new name now.


# References

bob van der staak. 17.11.2023. Evading Detection while using nmap. Infosec Write-ups. URL: https://infosecwriteups.com/evading-detection-while-using-nmap-69633df091f3. Accessed: 9.4.2025.

Caltagirone, S. 7.2013. The Diamond Model of Intrusion Analysis. Threat Intelligence Academy. URL: https://www.threatintel.academy/wp-content/uploads/2020/07/diamond-model.pdf. Accessed: 8.4.2025.

DavidJBianco. 17.1.2014. The Pyramid of Pain. Blogger - Enterprise Detection & Response. URL: https://detect-respond.blogspot.com/2013/03/the-pyramid-of-pain.html. Accessed: 8.4.2025.

hector adam. 11.3.2016. Where are Apache file access logs stored?. Unix & Linux Stack Exchange. URL: https://unix.stackexchange.com/questions/38978/where-are-apache-file-access-logs-stored. Accessed: 8.4.2025.

Karvinen, T. 26.3.2025. Verkkoon tunkeutuminen ja tiedustelu. Tero Karvinen. URL: https://terokarvinen.com/verkkoon-tunkeutuminen-ja-tiedustelu/. Accessed: 8.4.2025.

MDN web docs. 14.3.2025. An overview of HTTP. URL: https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Overview. Accessed: 8.4.2025.
