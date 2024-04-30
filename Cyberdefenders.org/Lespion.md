# Lespion
<a href="https://cyberdefenders.org/blueteam-ctf-challenges/lespion/"><img src="https://img.shields.io/badge/-Lespion-0072b1?&style=for-the-badge&logo=cyberdefenders&logoColor=white" /></a>

## Objective

The Lespion Lab project aimed to conduct a comprehensive investigation into a network compromise that had rendered a client's system offline. 
Utilizing Open Source Intelligence (OSINT), you delved into the incident to identify the attacker's identity and actions. 
Initial findings from incident responders suggested the attack stemmed from a single user account, potentially an insider, underscoring the necessity of meticulous examination.

### Skills Learned

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


Starting first in the lab is downloading the lab files which contains.  
Github.txt  
office.jpg  
WebCam.png  

 <img width="287" alt="Picture1" src="https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/f36475af-9f4d-4e3b-b03d-9fd432b96333">

<details>
<summary>Q1: File -> Github.txt: What is the API key the insider added to his GitHub repositories?</summary><br>
  
  -Upon opening the Github.txt we find the user account with the repository of the attack.  
  	![image004](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/e2ee46b7-caa9-4ef0-8989-2bf59665f13d)
  	  
  -This brings us to EMarseille99’s profile with 14 public repositories  
  	![image006](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/86eefb99-08e3-44fd-ab2b-a27755eaf04b)
  	  
  -Starting with the newest repository from May 24, 2020  
    ![image008](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/c9f67ace-0ad3-448e-9ce7-62086ee27daf)
  	  
  -We quickly locate the API key used in the attack on line 1  
    ![image010](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/d086d41f-6229-4a69-8740-b511e20c8e8a)
  	  
  -This will be the answer to our first question.  
    ![image012](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/78c56b03-decb-4ec2-9b3b-743e1c82437f)  

</details>

<details>
<summary>Q2 File -> Github.txt: What is the plaintext password the insider added to his GitHub repositories?</summary><br>
  
  -After looking through the same repository you come across  
  	![image014](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/20d69867-feed-4675-b6bf-bc539a2e857f)  
  	  
  -Which is the password saved in a base64 encoding, you can decode this by copying the encoded and using echo | base64 --decode while on kali.  
 	  ![image016](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/c6cc0395-95cd-4223-bf30-c9a4ad1c9f5b)  
  	  
  -Doing this gives you PicassoBaguette99  
 	  ![image018](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/60ab3fb7-7ae6-466a-b6b3-be925f13ae51)  
  	
</details>

<details>
<summary>Q3 File -> Github.txt: What cryptocurrency mining tool did the insider use?</summary><br>
  
   -After digging deeper into the rest of the repositories we come across an xmrig  
  
  -Which is a High performance, open source Miner  
    ![image020](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/7efa51a0-7350-4571-920e-efe0a1844f6c)  
  	
  -This is also the answer to the 3rd question.  
    ![image022](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/b3aa09c3-e955-4f27-bf49-0040e82dbfba)  

</details>

<details>
<summary>Q4 What university did the insider go to?</summary><br>
  
  -Moving on to the next questions we start to look for identifiers of the insider.  
  -Doing a standard google search of the username we are able to find an Instagram page as well as a LinkedIn profile.  
  -This is where we find that they went to Sorbonne Université  
    ![image024](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/388ae9e5-9a66-4538-9885-65fb4767313b)  

  -Which is the answer to question 4  
    ![image026](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/a76cb9ca-eeb8-461f-9854-b305b232e7e9)  

</details>

<details>
<summary>Q5 What gaming website the insider had an account on?</summary><br>

  -After doing some further searching I found a QR code on Instagram scanning that brings up their profile on Steam.  
     ![image028](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/709b5585-6a29-4a51-8018-85af831ff298)  
  	
  -Which is the answer to number 5.  
     ![image030](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/3c9de2bc-8f2b-4ace-af7e-5674d0ed6013)  

</details>

<details>
<summary>Q6 What is the link to the insider Instagram profile?</summary><br>
  
  -I have already been to their Instagram a few times already.  
     ![image032](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/9bc4c328-320c-42e0-9a8b-3d57dd03005b)  
  	
  -https://www.instagram.com/emarseille99/ is the correct answer to the question.  
	  ![image034](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/e7305a69-d62a-4737-806e-81a2c1c15077)  

</details>

<details>
<summary>Q7 Where did the insider go on the holiday? (Country only)</summary><br>
  
  -Using the photos and description from Instagram I was able to reverse image search to find that the insider went to Marina Bay Sands in Singapore.  
    ![image036](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/df624951-6b00-4516-9054-2a3794550155)  
  	
  -With the questions only wanting the country’s name Singapore was the correct answer.   
  ![image038](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/97ad34af-b990-4007-b7bc-a33c3a22d2b8)  

</details>

<details>
<summary>Q8 Where is the insider family live? (City only)</summary>

  -After looking through the Instagram photos we find the last 2 mention visiting family and friends.  
   	![image040](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/039ead0c-0261-41b9-9d6b-1382b5cf3fd1)  
    ![image042](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/26c150ac-f2ca-49d5-bedb-9bbb5ae7d36b)  

  -We are then able to use this second image and reverse lookup it again to find that it is near Burj Khalifa in Dubai  
    ![image044](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/ef2335ab-2c72-4604-adae-7f4286917080)  

</details>

<details>
<summary>Q9 File -> office.jpg: You have been provided with a picture of the building in which the company has an office. Which city is the company located in?</summary><br>
  
  -Going back to the images we recieved we have an office photo.  
    ![image046](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/10092b52-27e3-4ce8-b265-2d1761fa1c2e)  

  -Using this we can find that the office is next to the St Martin’s Church by Bull Ring found in Birmingham, England  
    ![image048](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/3665d164-63e5-47d9-9db6-b18c6ef47fd4)  

 -And we have now answered number 9  
    ![image050](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/bb82da8a-9de9-4f8d-b7e7-aa174a591d80)  

</details>

<details>
<summary>Q10 File -> Webcam.png: With the intel, you have provided, our ground surveillance unit is now overlooking the person of interest suspected address. They saw them leaving their apartment and followed them to the airport. Their plane took off and has landed in another country. Our intelligence team spotted the target with this IP camera. Which state is this camera in?</summary><br>
 
  -After a quick reverse search on the image I was able to identify it at Notre Dame University in Indiana.  
    ![image052](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/6084c99e-3aaf-4741-9dcc-4365fcac6eed)  

   -When looking at our last question it wants to know the state the target is in and the answer is Indiana as shown above.  
    ![image054](https://github.com/caseycolbert15/Cybersecurity-Labs/assets/165977507/051a2a8f-cfc2-4111-91e0-ea7d095cafbe)

</details>

<details>
<summary>Summary</summary>
Overall this was a very good LAB showing how useful it is knowing how to use Open Source Inteligence (OSINT) can be along with items that you might be looking for during a Threat intelligence search.
</details>
