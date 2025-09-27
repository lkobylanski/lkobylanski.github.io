---
layout: post
title: "[picoCTF] strings it – write-up"
tags: [ctf, picoCTF, writeup, beginner, forensics, linux]
---

# picoCTF – strings it  
**Author:** Łukasz Kobylański  
**Date of completion:** 2025-09-27  
**Difficulty level:** easy

---

## 1. Task Description
The challenge provided a file that should **not** be run. The goal is to obtain the flag from the file without executing it.

---

## 2. Objective
Extract the flag from the provided file without running it.

---

## 3. Work environment
- System: latest Kali Linux in VMware.  
- Tools & configuration: tmux (configuration borrowed from my mentor).  
- Work performed locally in a VM, using the terminal.

---

## 4. Solution steps (quick summary)
1. Locate the link/resource in the challenge interface (right-click / DevTools).  
2. Download the file to your machine using `wget`.  
3. Run `strings` on the downloaded file.  
4. Extract the flag from the output.

---

## 5. Solution — in detail
After opening the challenge page, the file containing the flag was available via a direct download link. We skip the hints for now and go straight to the download.  
I used RMB (right mouse button) to get the URL.  
![Screenshot – hint / link](/assets/img/ctf-2025-strings-it/get-url.png)  

Then I used `wget` with the link obtained in the previous step to download the file.  
![Screenshot – hint / link](/assets/img/ctf-2025-strings-it/download-file.png)  

Next I checked the file type — it was an executable named `strings`, and the challenge name was *"strings it"* — so let’s do it!  
![Screenshot – hint / link](/assets/img/ctf-2025-strings-it/file-strings.png)  

I ran the `strings` command. Many of you already know what this does, but I'll break it down a bit for those less familiar with Linux and to consolidate my own knowledge. As mentioned, the `strings` command scans a binary (or any) file and prints readable, printable character sequences (ASCII/Unicode) found inside. Thanks to this command we don't need to inspect raw hex.

If the file were plain text, it would be better to use `cat` or `less` directly. In this case I ran:

    strings strings | less

The pipe (`|`) redirects stdout from the command on the left into stdin for the command on the right, so the output is shown in `less`, where you can scroll.  
![Screenshot – hint / link](/assets/img/ctf-2025-strings-it/ls-strings-less.png)  

Inside `less` you can search immediately — from previous CTFs I already know the flag pattern. I searched for `picoCTF` by typing:

    /picoCTF
![Screenshot – hint / link](/assets/img/ctf-2025-strings-it/search-the-text.png)

And there it was — the challenge is completed! :)  
![Screenshot – hint / link](/assets/img/ctf-2025-strings-it/less_dislpayed.png)  

The flag was successfully extracted — redacted on the screen for public sharing.  
![Screenshot – hint / link](/assets/img/ctf-2025-strings-it/theFlag.png)  

![Screenshot – hint / link](/assets/img/ctf-2025-strings-it/win.png)  
