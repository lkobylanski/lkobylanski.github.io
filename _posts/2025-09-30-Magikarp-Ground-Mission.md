---
layout: post
title: "[picoCTF] Magikarp Grounded Mission"
tags: [ctf, picoCTF, writeup, beginner, linux]
---

# picoCTF – Magikarp Grounded Mission  
**Author:** Łukasz Kobylański  
**Date of completion:** 2025-09-30  
**Difficulty level:** easy  

---

## 1. Task Description
This challenge uses an *instance on demand*, meaning that the platform automatically spawns a temporary, isolated Linux environment (usually a container).  
Each instance comes with unique credentials (host, port, username, password) that are valid only for a limited time (about 30 minutes).  
I connected to this environment via SSH and navigated the file system to locate all parts of the flag.  

---

## 2. Objective
Get the full flag before the instance timer (30 mins) runs out.  

---

## 3. Work environment
- System: latest Kali Linux in VMware  
- Tools: tmux (configuration borrowed from my mentor)  
- Work performed locally in a VM, using the terminal  

---

## 4. Solution steps (quick summary)
1. Connect to the instance via SSH.  
2. Use `ls` to check files.  
3. Read `*.txt` files with `cat`.  
4. Follow instructions and move between `/`, `~`, and other directories.  
5. Combine flag parts into one string.  

---

## 5. Solution — in detail
After starting the challenge, the platform launched a 30-minute instance.  
![Screenshot – hint / link](/assets/img/ctf-2025-magikarp-ground-mission/1.png)  
![Screenshot – hint / link](/assets/img/ctf-2025-magikarp-ground-mission/2.png)  
On Kali I opened a terminal and connected via SSH (host, port, and password provided by picoCTF).  

Once connected, I ran `ls` and saw two files:  
- `1of3.flag.txt`  
- `instructions-to-2of3.txt`  

`cat 1of3.flag.txt` gave me the first part of the flag.  
The instructions file pointed me to the root directory `/`.  
![Screenshot – hint / link](/assets/img/ctf-2025-magikarp-ground-mission/3.png)  

I went there with `cd /` and ran `ls` again. Two new files appeared:  
- `2of3.flag.txt` (second part, yay :D)  
![Screenshot – hint / link](/assets/img/ctf-2025-magikarp-ground-mission/4.png)    
- `instructions-to-3of3.txt`  

I grabbed the second part with `cat` and checked the next instructions. They said:  
*"Lastly, ctf-player, go home… more succinctly `~`"*  
![Screenshot – hint / link](/assets/img/ctf-2025-magikarp-ground-mission/5.png)  

So I used `cd ~` to return to the home directory. Running `ls` there revealed the last file: `3of3.flag.txt`.  

Now it was time to combine everything. My first attempt was like this:  
cat /path/1of3 /path/2of3 /path/3of3
That printed each piece on a new line.

To get a single continuous string I used:  
cat /path/1of3 /path/2of3 /path/3of3 | tr -d '\n'

This removed line breaks and showed the full flag in one line. Challenge completed! :D  
![Screenshot – hint / link](/assets/img/ctf-2025-magikarp-ground-mission/6.png)  

![Screenshot – hint / link](/assets/img/ctf-2025-magikarp-ground-mission/7.png)  
## 6. Closing notes
Thanks for reading!  

P.S. As always, any comments on how I can improve (both content and description) are welcome.  
Special thanks to my mentors from the best cybersec school around :D  
**Maciej Kofel** and 🦡 **Jakub Domaradzki**
