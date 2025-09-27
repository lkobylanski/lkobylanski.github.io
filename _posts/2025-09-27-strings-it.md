---
layout: post
title: "[picoCTF] string it – write-up"
tags: [ctf, picoCTF, writeup, beginner, forensics, linux]
---

# picoCTF – string it  
**Author:** Łukasz Kobylański  
**Date of completion:** 2025-09-27  
**Difficulty level:** easy

---

## 1. Task Description
The challenge provided a file that should not be run. The goal is to obtain the flag from the file without running it.

---

## 2. Objective
Extract the flag from the provided file without running the file.

---

## 3. Work environment
- System: latest Kali Linux in VMware.
- Tools & configuration: tmux (configuration borrowed from my mentor).
- Work performed locally in a VM, using the terminal.

---

## 4. Solution steps (quick summary)
1. Locate the link/resource in the challenge interface (right-click / DevTools).
2. Download the file to your machine using wget.
3. Run strings command on downloaded file.
4. Extract flag from the text.

---

## 5. Solution — in details
After opening the challenge page, the file containing the flag was available via a direct download link. We are not checking hints so far, let's get directly to the download.
I use RMB click and obtain the url
![Screenshot – hint / link](/assets/img/ctf-2025-strings-it/get-url.png)  

Then I use wget and the link obtained in the previous step to download the file
![Screenshot – hint / link](assets/img/ctf-2025-strings-it/download-file.png)  

Then I check the file type - its executable file named strings - and the challegne name is "strings it" - let's do it!
![Screenshot – hint / link](/assets/img/ctf-2025-strings-it/file-strings.png)  

So I'm using strgins command - I know most of you knows exactly what I'mn doing here however I want to break it down a bit for those who are not familiar with Linux and are interested
And for myslef to consolidate knowledge. Ok so as mentioned before I'm using strings command, like this: strings strings | less
![Screenshot – hint / link](/assets/img/ctf-2025-strings-it/ls-strings-less.png)  
(strings command searches a binary file or any other file and prints out strings of readable, printable characters (ASCII/Unicode) that appear in the file. Thanks to this command we don't have to look into the hexadecimals).
In the other hand if file iss text file - its better to use cat or less directly on the file.
We use the command on the recently downloaded strings executable file. We use pipe to redirect stdout from the command on the left as stdin to the command on the right. 
The text instead to be shown directly in the terminal will be displayed in Less. Now we can scroll through the pages etc.
![Screenshot – hint / link](/assets/img/ctf-2025-strings-it/less_dislpayed.png)  

And we can search for specific terms rightaway - so fro m prevoious CTF I know how the flag pattern looks like. I use / to search in the text for string: picoCTF
![Screenshot – hint / link](/assets/img/ctf-2025-strings-it/search-the-text.png)  
And there it is! The challange is completed! :) 
The flag was successfully extracted — redacted on the screen for public sharing.
![Screenshot – hint / link](/assets/img/ctf-2025-strings-it/theFlag.png)  
![Screenshot – hint / link](/assets/img/ctf-2025-strings-it/win.png)  



