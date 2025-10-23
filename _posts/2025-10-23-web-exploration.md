layout: post
title: "CTF Pack WebExploration — 5x PicoCTF (two quick + one medium)"
date: 2025-10-09
categories: [CTF, picoCTF, writeups]
🧩 PicoCTF Pack — 5 Challenges form Web Exploration (3 medium + 2 easy)

A short write-up of three PicoCTF challenges solved today — two quick one-shots and one medium-level task.
Click each title below to expand the details.

Work environment
- System: Windows + Chrome newest version
- Tools: Burpsuite, DevTools, Cookie-Editor
- Work performed locally on my PC  

<details> <summary><b>1) insp3ct0r </b></summary>
Inspector
🔍 Description
 
First task from Web Exploration field. Here we will have to use DevTools to inspect the site and find the flag.

🛠️ What I did

Opened the page: 
<code>http://jupiter.challenges.picoctf.org:9670</code>
And I was on the page:
<img src="...assets/img/Web Exploration/insp3ct0r/5.png" width="600"> 
And I click on the HOW tab. Here we can see that to make this site creator used a HTML, CSS and JS.
<img src="..assets/img/Web Exploration/insp3ct0r/6.png" width="600"> 

1. I open DevTool (F12) and start inspecting DOM. Almost immediately I found 1st part of the flag in the HTML file:  
<img src="<img src="..assets/img/Web Exploration/insp3ct0r/1.png" width="600"> " width="600">  

2. Then I move to sources and check mycss.css where I found 2nd part of the flag  
<img src="..assets/img/Web Exploration/insp3ct0r/5.png" width="600"> 

3. And then move to myjs.js where the last part of the flag is waiting. 
<img src="../assets/img/ctf-2025-whats-netcat/2.png" width="600">  

</details>
<details> <summary><b>2) Where are the robots? </b></summary>
 Where are the robots?
🔍 Description
 
Pretty simple challenge. As the name indicates we will be checking robots.txt file  

🛠️ Steps

1. I open an URL given in the task, and I add at the end of it /robots.txt 
(<i>a text file that website owners create to tell web crawlers (like search engine bots) which pages or directories on their site should not be crawled</i>)  
<img src="assets/img/Web Exploration/where are the robots/1.png" width="600">  

2. In the robot.txt we can see disallow file.html. I puit it at the end of the URL:  
<img src="assets/img/Web Exploration/where are the robots/2.png" width="600">  

And we got the 2nd flag:  
<img src="../assets/img/ctf-2025-warm-up/2.png" width="600">

</details>
<details> <summary><b>3) GET A HEAD (medium)</b></summary>
GET A HEAD — (medium)
🔍 Description

A medium-level challenge involving the Burp Suite to manipulate the HTTPS requests.

🛠️ Steps to solve

1. Open the link from the task: http://mercury.picoctf.net:21939/
<img src="../assets/img/Web Exploration/GET A HEAD/4.png" width="600">

2. The site changes color accordingly to the button we click. If we click blue option there is POST request, when red there is a GET  
BLUE:
<img src="../assets/img/Web Exploration/GET A HEAD/5.png" width="600">

RED:
<img src="../assets/img/Web Exploration/GET A HEAD/6.png" width="600">

3. As the title of the challenge is GET a HEAD - I assume the GET is the request we want to experiment with. I intercept GET request and switch GET for HEAD - as in the challenge title and send
And there it is! The flag:
<img src="../assets/img/Web Exploration/GET A HEAD/3.png" width="600">

</details>
<details> <summary><b>4) Cookies (medium)</b></summary>
Cookies — (medium)
🔍 Description
TO BE ADDED

🛠️ Steps to solve

1.

2. 

3.

</details>
<details> <summary><b>5) Scavenger Hunt (medium)</b></summary>
Cookies — (medium)
🔍 Description
TO BE ADDED

🛠️ Steps to solve

1.

2. 

3.

</details>
