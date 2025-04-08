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




# References

Caltagirone, S. 7.2013. The Diamond Model of Intrusion Analysis. Threat Intelligence Academy. URL: https://www.threatintel.academy/wp-content/uploads/2020/07/diamond-model.pdf. Accessed: 8.4.2025.

DavidJBianco. 17.1.2014. The Pyramid of Pain. Blogger - Enterprise Detection & Response. URL: https://detect-respond.blogspot.com/2013/03/the-pyramid-of-pain.html. Accessed: 8.4.2025.

hector adam. 11.3.2016. Where are Apache file access logs stored?. Unix & Linux Stack Exchange. URL: https://unix.stackexchange.com/questions/38978/where-are-apache-file-access-logs-stored. Accessed: 8.4.2025.

MDN web docs. 14.3.2025. An overview of HTTP. URL: https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Overview. Accessed: 8.4.2025.
