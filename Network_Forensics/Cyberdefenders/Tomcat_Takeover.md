# Tomcat Takeover
<a href="https://cyberdefenders.org/blueteam-ctf-challenges/tomcat-takeover/"><img src="https://img.shields.io/badge/-Tomcat_Takeover-0072b1?&style=for-the-badge&logo=cyberdefenders&logoColor=white" /></a>

## Objective

Our SOC team has detected suspicious activity on one of the web servers within the company's intranet.
In order to gain a deeper understanding of the situation, the team has captured network traffic for analysis.
This pcap file potentially contains a series of malicious activities that have resulted in the compromise of the Apache Tomcat web server.
We need to investigate this incident further.  

### Skills Learned

- Utilize a Packet Analysis Tool
  - Gain an understanding of how a Packet Analysis tool works
- Interpret network traffic patterns
- Identify common protocols and their corresponding traffic
- Recognize anomalies or suspicious patterns in network traffic

### Tools Used

- Wireshark
- NetworkMiner

## Write up

<details>
<summary>Q1 Given the suspicious activity detected on the web server, the pcap analysis shows a series of requests across various ports, suggesting a potential scanning behavior. Can you identify the source IP address responsible for initiating these requests on our server?</summary><br>

  -Wireshark allows us to view converstions by going to the upper menu Statistics->Conversations  
    ![Question1a](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/c73cad5c-c5d9-40ee-a8fe-7fe75123ad80)  

  -From here we can go to TCP conenctions and see that IP address 14.0.0.120 has been running a port scan on 10.0.0.112  
    ![Question1b](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/29fbfe3a-3864-4f69-8a8b-4baecd903469)  

  -This IP address will be our answer for number 1.  
    ![Question1c](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/56d7cf77-ff5d-41f0-a76b-c240bd483518)  

</details>

<details>
<summary>Q2 Based on the identified IP address associated with the attacker, can you ascertain the city from which the attacker's activities originated?</summary><br>

  -Since the IP address is a public IP we can run an IP lookup to get Guangzhou as the City  
    ![Question2a](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/422d3477-3e1f-498b-8c91-fcfa1f76bf15)  

  -Which is our answer for questions 2.  
    ![Question2b](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/347946fd-8018-4b93-9279-a0c275683eb9)  

</details>

<details>
<summary>Q3 From the pcap analysis, multiple open ports were detected as a result of the attacker's activitie scan. Which of these ports provides access to the web server admin panel?</summary><br>

  -Moving on to our analysis of the packets we want to first set our filter to ip.addr==14.0.0.120 this will only show only packets that either have this IP address as a the sender or reciever.  
  -You could also use the filter ip.src==14.0.0.120 this will show you packets sent from this IP address.  
    -Since Wireshark has a colorization template you can tell the non accepted traffic from accepted traffic.  
  -Here we can see that most ports are returning a RST flag which is colored red.  Meaning that these ports are not open.  
  -After going past these errors we finally come across traffic that has been accepted (in light purple and green) and communicating on port 8080.  
    ![Question3a](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/09337251-277e-4311-9536-00ce42b5a3ec)  

  -This port will be our answer for question 3  
    ![Question3b](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/41f9190f-f4ea-4b9e-ab73-5f4b0f15d8a9)  

</details>

<details>
<summary>Q4 Following the discovery of open ports on our server, it appears that the attacker attempted to enumerate and uncover directories and files on our web server. Which tools can you identify from the analysis that assisted the attacker in this enumeration process?</summary><br>

  -Here we are looking for the User-Agent field from the accepted traffic.  
  -Once you start to see a patern with GET attempts we can look at one of these packets to find that gobuster is used as the tool.    
    ![Question4a](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/3ea78c38-3b01-43e0-961a-7b457fc0bbcb)  

  -If you have trouble finding the packets you can also filter by  

    ip.addr==14.0.0.120 && http.user_agent  

  -This will only return packets that are from IP 14.0.0.120 and packets that have something in the User-Agent field.  
    ![Question4c](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/9d6ba1ec-653b-44ce-a46e-c9736a0d4c57)  

  -Entering gobuster will give us our answer to question 4.  
    ![Question4b](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/c4db1853-d38c-429a-b926-7ee8500d8492)  

</details>

<details>
<summary>Q5 Subsequent to their efforts to enumerate directories on our web server, the attacker made numerous requests trying to identify administrative interfaces. Which specific directory associated with the admin panel was the attacker able to uncover?</summary><br>

  -filtering with the http.user_agent we can find that the attempts made after gobuster has ran.  
  -This shows that /example was able to be accessed but is not the admin interface.  
  -Right after this we also see /manager attempting to be connected to with admin credentials representing an admin console.  
    ![Question5a](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/a25960ae-7ece-4047-b197-81239ec14755)  

  -Using /manager will give our answer for queston 5.  
    ![Question5b](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/a6b62168-53ce-4ade-ac64-fa86aa30767f)  

</details>

<details>
<summary>Q6 Upon accessing the admin panel, the attacker made attempts to brute-force the login credentials. From the data, can you identify the correct username and password combination that the attacker successfully used for authorization?</summary><br>

  -Looking through the attempts to access manager we can see many failed attempts at the password.  
  -However it does eventually connect, looking at the authorization information in the packet we can see they used admin:tomcat  
    ![Question6a](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/b7c1e9be-843d-41e6-b1c5-27b7ad3cecd6)  

  -Using the credentials in this format gives us the answer for question 6.  
    ![Question6b](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/0c456c47-2d29-47e5-a443-544d62982b8e)  

</details>

<details>
<summary>Q7 Once inside the admin panel, the attacker attempted to upload a file with the intent of establishing a reverse shell. Can you identify the name of this malicious file from the captured data?</summary><br>

  -Since this question involves uploading to the computer we want to look for a POST command which sends data to the target IP.  
  -Here we find the packet and after looking at the data in the packet we find a file name JXQOZY.war was uploaded to /manager  
    ![Question7a](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/92495ee8-b2c7-4796-ad9d-d1b8078da9e5)  

  -JXQOZY.war will be our answer for questions 7.  
    ![Question7b](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/6281ce9e-0f0c-4b1d-bdf1-88b65f4979de)  

</details>

<details>
<summary>Q8 Upon successfully establishing a reverse shell on our server, the attacker aimed to ensure persistence on the compromised machine. From the analysis, can you determine the specific command they are scheduled to run to maintain their presence?</summary><br>

  -From here we need to determine what commands were sent to the victims PC.  
  -Payloads sent are sent as TCP payloads, we can find these a few different ways.  
  -We can use a filter to only include packets with a TCP payload  

    ip.addr==14.0.0.120 && tcp.payload  

  -Doing this we can see the packets and the payload of each packet sent to find the commands used.  
    ![Question8e](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/01e04b3f-be63-417f-8268-09422e75948c)  

  -Or what would likely be easier is to find one of these packets and select follow TCP Stream.  
    ![Question8a](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/a35199a8-42b6-4f68-b152-567268f4f03c)  

  -This will show us all the data that went along with that connection session.  
    ![Question8b](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/64c02308-f17a-4ab4-8eb6-a7b02739c856)  

  -Once we have pulled up the stream we can see the /bin/bash command, copying that command will give us our final answer.  
    ![Question8d](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/32b294c4-47c3-4e7a-b9eb-61865e64185f)  

</details>

<details>
<summary>Summary</summary><br>

This was a very well designed and relatively simple lab that allowed you to explore the functions of a packet analizer.
There were many other techniques and filters that could have been used to more quickly find some of the answers that I did not go over.
This lab also shows how essential it is to know how to use a packet analizer and what IOCs to look for during your hunt.

</details>


