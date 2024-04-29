# Lespion

## Objective
Identify the insider

The Lespion Lab project aimed to conduct a comprehensive investigation into a network compromise that had rendered a client's system offline. Utilizing Open Source Intelligence (OSINT), you delved into the incident to identify the attacker's identity and actions. Initial findings from incident responders suggested the attack stemmed from a single user account, potentially an insider, underscoring the necessity of meticulous examination.


### Skills Learned
[Bullet Points - Remove this afterwards]

- Open Source Intelligence (OSINT) Analysis:
  - Gather and analyze information from publically available sources to uncover insights.  
- Incident Investigation:
  - Conduct a through investigation into the security incident to identify the root cause and responsible parties.  
- Communication Skills:
  - Effective communication skills to convey the findings and recommendations to stakeholders

### Tools Used

- Github
- Chrome
- Google reverse image search

## Write up


Starting first in the lab is downloading the lab files which contains. <br>
Github.txt <br>
office.jpg <br>
WebCam.png <br>

 <img width="287" alt="Picture1" src="https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/f36475af-9f4d-4e3b-b03d-9fd432b96333">


1.	The first question is asking for the API key from the github users account.

Upon opening the Github.txt we find the user account with the repository of the attack. <br>
 ![image004](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/e2ee46b7-caa9-4ef0-8989-2bf59665f13d)


This brings us to EMarseille99’s profile with 14 public repositories<br>
 ![image006](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/86eefb99-08e3-44fd-ab2b-a27755eaf04b)


Starting with the newest repository from May 24, 2020<br>
 ![image008](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/c9f67ace-0ad3-448e-9ce7-62086ee27daf)


We quickly locate the API key used in the attack on line 1<br>
 ![image010](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/d086d41f-6229-4a69-8740-b511e20c8e8a)


This will be the answer to our first question.<br>
 ![image012](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/78c56b03-decb-4ec2-9b3b-743e1c82437f)


2.	 The second question is asking for the plaintext password used in the same Login Page.js
After looking you come across <br>
![image014](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/20d69867-feed-4675-b6bf-bc539a2e857f)


Which is the password saved in a base64 encoding, you can decode this by copying the encoded and using echo | base64 --decode while on kali.  <br>
![image016](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/c6cc0395-95cd-4223-bf30-c9a4ad1c9f5b)


Doing this gives you PicassoBaguette99<br>
 ![image018](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/60ab3fb7-7ae6-466a-b6b3-be925f13ae51)


3.	The next question is asking for the cryptocurrency mining tool used.<br>
After digging deeper into the rest of the repositories we come across an xmrig<br> 

Which is a High performance, open source Miner<br>
 ![image020](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/7efa51a0-7350-4571-920e-efe0a1844f6c)


This is also the answer to the 3rd question.<br>
 ![image022](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/b3aa09c3-e955-4f27-bf49-0040e82dbfba)


4.	Moving on to the 4th we start to look for them personally this question is asking us where they went to school.<br>

Doing a standard google search we are able to find an Instagram page as well as a LinkedIn profile.<br>
This is where we find that they went to Sorbonne Université<br>
![image024](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/388ae9e5-9a66-4538-9885-65fb4767313b)


Which is the answer to question 4<br>
 ![image026](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/a76cb9ca-eeb8-461f-9854-b305b232e7e9)


5.	Moving to question 5 we are now looking for the gaming website the insider had an account on.<br>
After doing some further searching I found a QR code on Instagram scanning that brings up their profile on Steam. <br>
![image028](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/709b5585-6a29-4a51-8018-85af831ff298)

 
Which is the answer to number 5. <br>
 ![image030](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/3c9de2bc-8f2b-4ace-af7e-5674d0ed6013)


6.	Number 6 is wanting to know the website of their Instagram page which I have been to a few times already. <br>
![image032](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/9bc4c328-320c-42e0-9a8b-3d57dd03005b)


https://www.instagram.com/emarseille99/ is the correct answer to the question.<br>
 ![image034](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/e7305a69-d62a-4737-806e-81a2c1c15077)


7.	This is asking the country that she went to on vacation, using the photo in the top right corner I was able to reverse image search to find that she went to Marina Bay Sands in Singapore<br>
![image036](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/df624951-6b00-4516-9054-2a3794550155)

 
With the questions only wanting the country’s name Singapore was the correct answer.<br>
 ![image038](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/97ad34af-b990-4007-b7bc-a33c3a22d2b8)


8.	For number 8 we are trying to find the city that the insiders family lives in/by.<br>
After looking through the Instagram photos we find the last 2 mention visiting family and friends.<br>
  ![image040](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/039ead0c-0261-41b9-9d6b-1382b5cf3fd1)<br>
![image042](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/26c150ac-f2ca-49d5-bedb-9bbb5ae7d36b)


We are then able to use this second image and reverse lookup it again to find that it is near Burj Khalifa in Dubai <br>
![image044](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/ef2335ab-2c72-4604-adae-7f4286917080)


9.	Questions 9 asks us where the office is located, if we remember back before question 1 we had 2 photos 1 of which was an office photo.<br>
![image046](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/10092b52-27e3-4ce8-b265-2d1761fa1c2e)


Using this we can find that the office is next to the St Martin’s Church by Bull Ring found in Birmingham, England <br>
![image048](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/3665d164-63e5-47d9-9db6-b18c6ef47fd4)

 
And we have now answered number 9<br>
 ![image050](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/bb82da8a-9de9-4f8d-b7e7-aa174a591d80)


10.	The last question is having us find where the suspect currently is base on the WebCam image provided. <br>
After a quick reverse search on the image I was able to identify it at Notre Dame University in Indiana. <br>

 ![image052](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/6084c99e-3aaf-4741-9dcc-4365fcac6eed)

When looking at our last question it wants to know the state the target is in and the answer is Indiana as shown above.<br>

![image054](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/051a2a8f-cfc2-4111-91e0-ea7d095cafbe)

 
Overall this was a very good LAB showing how useful it is knowing how to use Open Source Inteligence (OSINT) can be along with items that you might be looking for during a Threat intelligence search.
