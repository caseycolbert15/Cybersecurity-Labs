# Network Analysis - Web Shell
<a href="https://blueteamlabs.online/home/challenge/network-analysis-web-shell-d4d3a2821b"><img alt="Blue Team Labs" src="https://img.shields.io/badge/Blue Team Labs-14164a?&style=for-the-badge&logo=data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABIAAAASCAYAAABWzo5XAAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAAAJcEhZcwAADsMAAA7DAcdvqGQAAAQVSURBVDhPdZN/bFNVFMfPfX196+9n2/2SRelgsHXsR+YaUdTBkBriwg8FBZXo/LGFKSohMdF/plEJmIASY4CEHxKCmhQZOF0MuB+6jWVjG6tr2QhzsHUdnXulW/ve2te+vnd97YphRD95yX3nfM+5OfeecxHcB8aYPHm6eY3LPVacmW6YWvtcWROYcgxtfryeR0hVrlf2bHhQ2Y8QklIpSRZs1NExaDxy4tL54Rve1fl5OTDpC4A2O91P1FZrdGpKo1EgGA/HpVK94swOs67OloPCqdSF1L1/+MuqLZ/iaWYWSxLGET6GD3zbghvGORyXbfnDw2wcb+wJih8PsbtSaUmI1AoMw+g9HuaNN1+1Q0Y6DbNBDq4NeYAMh4HtvALDwx7gIzHI1ylgXQZFeKOo1iNJ6lT6/EZHjv38aPXOo4P+AEuXleYmhYvNAxCYYWHtlkpoX2SFQ21/wdD1ieRdPEKTMBYRi+qdXPdJT7Q4EU+MBgJ0w0+9jWUluZaWps/Bsjgr4Yc0JQmrVhYApVWDg1XDtYzFIF9wUltlIuGsTY+yVIqSS0zsPMNIeuLsqTZ7TIhn1X+0DbTatGTgXXBqTXBvVxL/RiWCD/PUEIpjiyMYriCCs6zZbNIDSSrmo1IoKRJuy11LoJWlkmgAVCpl0r6LSu6ingAiJIKZsFofco17pvGE15+S56msKIZzF7rgzy4XVE8PQrk0C8vzFqXUeUY4Ee4IWFiuU7qRw+FQ/Nrq+25iwv/irp1VyGw2ACHXnjgWzwvQPXATMssLYUWhRa56vsmSLHp5CU5P8NIyDXH8YJGuLnn03/pG6dbGjk96ekfWx0VJI8ZFbTAUNhqN+ilep8swvlcTI9Vp4ZCA02kKTSsA8RQBrI0mflxJaw9WZiFO4XZj6swpxxdXnTftpcWW7pq6Z3ZoyLQxry+w5u3X7ZVBRNlLS3JbC02q/ZNRvGF7NvXC6izyMMPjMhcnVnCSmNn+zd52sqn13LO9AyPv7Hl3Ezpw6EJBiItmC0LckBjjuTnsRwSICKRIlEABAQN5lZU+YGckg2w8/nKOCh338PnHbvF/EBEuRqvSKFRalAsURaKpqUDBHBcxrbA+3KXXKzIC/tADTFyxdAmJI8u0hHNGkBbPCNiiJwlklaeclGeRE+M0dAwOGre+sq/b9tSe4PMv7bvcM+Q1y09K6fP5tJu37e3b9NbXeGPnHWm3iz0h+6mE1nCbt27vDbnsXaHZGifXfEOSDMkueDyS+oeGzqWTk5OapEPm4mVnZvkTu2f6naP4e28Ub74S6pcT/p3YRPIvU5EltzBWpVz/TV8fVr5W+1XTk1v3i+t+Z4T663OfydXcO+AL+F8hgdv9t66xc6DK9PRjQVse3WJDSEhJ9wHwD6KG2vagb6UcAAAAAElFTkSuQmCC" />

## Objective

The SOC received an alert in their SIEM for ‘Local to Local Port Scanning’ where an internal private IP began scanning another internal system. Can you investigate and determine if this activity is malicious or not? You have been provided a PCAP, investigate using any tools you wish. I chose Wireshark.

### Skills Learned

- Utilize a Packet Analysis Tool
  - Gain an understanding of how a Packet Analysis tool works
- Interpret network traffic patterns
- Identify common protocols and their corresponding traffic
- Recognize anomalies or suspicious patterns in network traffic

### Tools Used

- Wireshark

## Write up

Start the lab by downloading the lab files which contains the .pcap file.    
BTLOPortScan.pcap  

<details>
<summary>Q1: What is the IP responsible for conducting the port scan activity?</summary><br>

  -Wireshark allows us to view converstions by going to the upper menu Statistics->Conversations->TCP where we see that there were 1284 connections.  
    <img width="583" alt="Picture1" src="https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/136e755d-8cbe-4f87-b981-584ced7527d1">  
  	  
  -While in connections we can sort by Port B which will show us the ports that Address A is trying to reach.  
    <img width="314" alt="Picture2" src="https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/f2ef3a5e-0a25-44d5-a476-a6ae1c6e19b0">  

  -Here we can see that IP Address 10.251.96.4 is running a port scan on 10.251.96.5 which is the answer to questions 1  
    <img width="487" alt="Picture3" src="https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/595da9a9-73a9-48f7-9130-65cf6da0914e">  
</details>

<details>
<summary>Q2: What is the port range scanned by the suspicious host?</summary><br>
    
  -From that connections page we can sort by asc or desc allowing us to see that the ports range from 1-1024.  
  -The answer to number 2  
    <img width="481" alt="Picture4" src="https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/476618cf-a270-41de-a39a-abb156cdfe17">  
</details>

<details>
<summary>Q3: What is the type of port scan conducted? </summary><br>

  -Closing the Connections window and going back to the scanned traffic we find many SYN packets being sent from the IP 10.251.96.4 using TCP
    <img width="1069" alt="Picture5" src="https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/7c705b07-af03-4307-8714-bf903626277b">  

  -Using this information we can determine that the scan happening is likely a TCP SYN scan.  
    -This is a scan that sends a SYN request to every port, if the ACK flag is then recieved, a Reset command (RST) is sent and the port is then noted to be open.  
    -If an RST flag is recieved or nothing replies the port is marked as closed.  
      -Learn more at [nmap.org](https://nmap.org/book/synscan.html)  
        <img width="594" alt="Picture6" src="https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/d3273865-9713-43b3-a1f4-79bd6aba431d">  
        <img width="589" alt="Picture7" src="https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/878ddf97-a9ee-4705-80a0-9589fdbf2c64">  

  -Using TCP SYN gives us the correct answer to questions 3.  
    <img width="399" alt="Picture8" src="https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/51d5b23e-a2b7-466a-bc12-11a39a1911a8">  

</details>

<details>
<summary>Q4 Two more tools were used to perform reconnaissance against open ports, what were they?</summary><br>

  -Since we know the IP source and destination we can add that to our filter to get only the requests we want to see.  
  
    -ip.src == 10.251.96.4 && ip.dst == 10.251.96.5  
  -By doing this we can scroll through all the requests and we will eventually start to see a pattern of different GET attempts.  
  -When opening one of these packets we can check under the HTTP request and see the User-Agent field has gobuster/3.0.1 which will be our fist tool.  
    <img width="1078" alt="Picture9" src="https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/0f721bbd-0558-4d21-9c2c-7752e17b66ce">  

  -Moving past the GET attempts we will then come across several POST requests and looking at these we can see the User-Agent as sqlmap/1.4.7, our second tool.  
    <img width="1072" alt="Picture10" src="https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/246ab285-6522-4df5-8422-a22a53920a57">  

  -Inputting these will give us the correct answer to question 4.  
    -Make sure you put it in the syntax that they ask for.  
    <img width="694" alt="Picture11" src="https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/42505dd6-f18b-4454-8298-75fa4ce767d6">  

  -If you have trouble finding the packets with the User-Agent you can also filter for only packets that contain a user agent by using the following filter.  

    -ip.dst == 10.251.96.5 && http.user_agent  
  <img width="1067" alt="Picture12" src="https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/804c4604-0192-4215-83ac-2660f603f740">
  
</details>

<details>
<summary>Q5 What is the name of the php file through which the attacker uploaded a web shell?</summary><br>

  -Since we are specifically looking for a file that was uploaded we can add the http.request.method==POST to our filter  
    <sub>-The POST method sends data to the server</sub>  

    -ip.src == 10.251.96.4 && ip.dst == 10.251.96.5 && http.request.method==POST  
  -At the very bottom of the packets we find a /upload.php, however, do not get confused as this is not the name of the file used.  
  -Double clicking on the file to open it and take a deeper dive we find that the referer file is actually the editprofile.php  
    <img width="661" alt="Picture13" src="https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/d57a2b8d-577d-457f-a61e-76177fcc2229">  

  -editprofile.php is indeed our answer to question 5  
    <img width="634" alt="Picture14" src="https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/0b261c01-830f-4b8a-93a0-ae13c8444023">  
  
</details>

<details>
<summary>Q6 What is the name of the web shell that the attacker uploaded?</summary><br>

  -Since we now know when they uploaded the file (event 16102) we can go to our previous filter with just the src and dst IP addresses.  
  -Moving just past the /upload.php event, we come across an /uploads/dbfunctions.php and then a second dbfunctions with a cmd line after it.  
  -This tells us that the shell(malicious file) the attacker is using is the dbfunctions.php file  
    <img width="1486" alt="Picture15" src="https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/98cdbb68-1518-4122-8e92-d4dadfc68a5e">  

  -Answer to questions 6  
    <img width="520" alt="Picture16" src="https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/b6317810-2545-45f6-92c1-a08646a3f0c4">  
  
</details>

<details>
<summary>Q7 What is the parameter used in the web shell for executing commands?</summary><br>

  -As we just discussed in question 6 the parameters being used with the shell is the cmd(command line)  
    <img width="1486" alt="Picture15" src="https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/a7287ace-0115-4eb0-a5ce-364611f86cec">  

  -Answer to question 7  
    <img width="561" alt="Picture17" src="https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/489316e5-ab5e-42ca-bfc3-b169c4bcf710">  
  
</details>

<details>
<summary>Q8 What is the first command executed by the attacker?</summary><br>

  -Once again looking at our previous screenshot we can see that the first command ran with cmd is cmd=id  
    <img width="1486" alt="Picture15" src="https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/8dc98a33-4a37-4390-a65f-79aa0ef2ab00">  

  -Answer to questions 8  
    <img width="447" alt="Picture18" src="https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/abd4393a-50c5-4fdc-9d7b-f6157ea44fb5">  
  
</details>

<details>
<summary>Q9 What is the type of shell connection the attacker obtains through command execution?</summary><br>

  -For questions 9 we are going to need to take a deeper look at the last /upload command  
  -Here we can see the command being ran is a python script that is set to have the victims computer at 10.251.96.5 connect back to the attacking device at 10.251.96.4  
    <img width="1565" alt="Picture19" src="https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/d86f4027-25cd-469e-aefe-0470ab570daf">  

  -This is what is called a reverse shell where you have the victims computer connect to the attackers to give them full control.  
  -This will be our answer for question 9  
    <img width="672" alt="Picture20" src="https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/6fd7a007-a5dc-4123-80a4-7282f66e43ce">  

</details>

<details>
<summary>Q10 What is the port he uses for the shell connection?</summary><br>

  -With the previous screenshot we can also see that the port used to make the connection was done over port 4422.  
    <img width="1565" alt="Picture19" src="https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/d86f4027-25cd-469e-aefe-0470ab570daf">  

  -This will be our final answer of the lab.  
    <img width="414" alt="Picture21" src="https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/e9b7d5ec-b268-4a1c-918d-3c5a18662fdf">  

</details>

<details>
<summary>Summary</summary><br>

This was a very well designed and relatively simple lab that allowed you to explore the functions of a packet analizer.  
There were many other techniques that could have been used to find some of the answers that I did not go over.  
For instance you could have done a find packet and searched for .php or cmd which would have immediately taken you to the files and commands used.  
We can also see from this lab how essential it is to know how to use a packet analizer and what IOCs to look for during your hunt.  
  
</details>














