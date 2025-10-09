layout: post
title: "CTF Pack — 3x PicoCTF (two quick + one medium)"
date: 2025-10-09
categories: [CTF, picoCTF, writeups]
tags: [picoctf, writeup, netcat, forensics, beginner, medium]
🧩 PicoCTF Pack — 3 Challenges (1 medium + 2 quick)

A short write-up of three PicoCTF challenges solved today — two quick one-shots and one medium-level task.
Click each title below to expand the details.

<details> <summary><b>1) what's a net cat</b></summary>
what's a net cat
🔍 Description
It was warm up before medium level CTF I'm gonna take today.
To find the flag we will need to use then netact (nc) linux command.

🛠️ What I did
Connected to the host *****:
<code>nc host.example.com 12345</code>

Received response from a server containing the flag.

📸 Screenshot  
<img src="../assets/img/ctf-2025-whats-netcat/1.png" width="600">  
🏁 Flag
<code>picoCTF{PLACEHOLDER_WHATS_A_NET_CAT}</code>  
And the task was completed.  
<img src="../assets/img/ctf-2025-whats-netcat/2.png" width="600">

</details>
<details> <summary><b>2) Lets Warm Up</b></summary>
Lets Warm Up
🔍 Description

A very basic warm-up challenge — likely reading a file or doing a simple conversion.

🛠️ Steps (placeholder)

Downloaded the file:
<code>wget http://example.com/flag.txt
 -O flag.txt</code>

Displayed the contents:
<code>cat flag.txt</code>

📸 Screenshot
<img src="../assets/img/ctf/lets-warm-up.png" alt="lets warm up screenshot" width="600">
🏁 Flag

<code>picoCTF{PLACEHOLDER_LETS_WARM_UP}</code>

</details>
<details> <summary><b>3) Nice netcat (medium)</b></summary>
Nice netcat — (medium)
🔍 Description

A medium-level challenge involving netcat and ASCII conversion — we receive a stream of numbers (space-separated) that must be translated to readable text.

🛠️ Steps to solve

Connected to the server:
<code>nc mercury.picoctf.net 35652</code>

Saved the output to a file:
<code>nc mercury.picoctf.net 35652 > nice_netcat_spaces_flag.txt</code>

The file contained space-separated decimal numbers — I converted each number to its ASCII character:
<code>awk '{ for(i=1;i<=NF;i++) printf "%c", $i; print "" }' nice_netcat_spaces_flag.txt > decoded.txt</code>
Alternatively, if numbers are in decimal format:
<code>tr ' ' '\n' < nice_netcat_spaces_flag.txt | while read num; do printf "\x$(printf %x $num)"; done ; echo</code>

Read the decoded file and retrieved the flag.

📸 Screenshots
<img src="../assets/img/ctf/nice-netcat-1.png" alt="nice netcat step 1" width="600"> <img src="../assets/img/ctf/nice-netcat-2.png" alt="nice netcat step 2" width="600">
🏁 Flag

<code>picoCTF{PLACEHOLDER_NICE_NETCAT}</code>

🔁 Notes / Takeaways

AWK is incredibly efficient for iterating over fields and converting numeric values to characters.

Always check the number format (decimal / hex / octal) before converting.

</details>
