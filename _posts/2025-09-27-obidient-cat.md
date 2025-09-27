---
layout: post
title: "[picoCTF] Obedient Cat – write-up"
tags: [ctf, picoCTF, writeup, beginner, forensics, linux]
---

# picoCTF – Obedient Cat  
**Author:** Łukasz Kobylański  
**Date of completion:** 2025-09-25  
**Difficulty level:** easy

---

## 1. Task Description
The challenge provided a file that supposedly contained the flag in plain sight – meaning the flag was not hidden or obfuscated, but directly readable. The objective was to download the file and extract the flag from it.

---

## 2. Objective
Wyodrębnić flagę z dostarczonego pliku.

---

## 3. Work environment
- System: najnowsze Kali Linux w VMware.  
- Narzędzia i konfiguracja: tmux (konfiguracja zapożyczona od mentora).  
- Praca lokalna w VM, terminal.

---

## 4. Solution steps (quick summary)
1. Locate the link/resource in the challenge interface (right-click / DevTools).
2. Download the file to your machine.
3. Check the file type (it turned out to be a plain text file).
4. Read the flag with cat / open the file in an editor.

---

## 5. Solution — in details
After opening the challenge page, the file containing the flag was available via a direct download link.
![Screenshot – hint / link](/assets/img/ctf-2025-obidient-cat/obidient-cat-main-screen.jpg)

Link was available in the 2nd hint.
![Screenshot – hint / link](/assets/img/ctf-2025-obidient-cat/hint2url.jpg)
However it was not necessary to get it, we could just click RMB and copy link
![Screenshot – hint / link](/assets/img/ctf-2025-obidient-cat/getUrlYourself1.jpg)
or obtain it from the href in DOM.
![Screenshot – hint / link](/assets/img/ctf-2025-obidient-cat/getUrlYourself2.jpg)

I fetched the file to my VM using wget command and obtained URL
![Screenshot – hint / link](/assets/img/ctf-2025-obidient-cat/wget.jpg)
I verified its type (it turned out to be plain ASCII text)
```html
<p align="left">
  <img src="/assets/img/ctf-2025-obidient-cat/file-flag.jpg" alt="screenshot 1" style="max-width:100%;height:auto;">
</p>
```
and then inspected its contents using standard Linux cat command (We can see that the name of the challange indicated at very beggining that we will need cat command ;) ). 
The flag was successfully extracted — redacted on the screen for public sharing.
![Screenshot – hint / link](/assets/img/ctf-2025-obidient-cat/getUrlYourself2.jpg)
