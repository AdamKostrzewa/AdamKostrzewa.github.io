---
layout: post
title:  "[ENG] Presentation from Confidence 2020 - You can also design and test your hardware trojan! Exploiting a CPU Backdoor for x86 Architecture."
date:   2020-09-11 08:38:12 +0200
categories: jekyll update
---
Below you may find my presentation from the Confidence 2020.
[Confidence 2020](https://confidence-conference.org/lecture.html#id=61981) Conference Site
Feel free to contact me if you have any questions or doubts   

PDF for download: [Downlad](/download/akostrzewa_confidence2020.pdf) 

<iframe src="https://drive.google.com/file/d/1I_hTNdn-2h9GA6MBxki7SRlK56h53MfK/preview" width="1000" height="500"></iframe>

  

**Abstract**:

How difficult it is to introduce a hardware trojan or backdoor into a modern electronic equipment? How attacker can exploit such threats and extract your data? What are the principles of work of such circuits? If these questions are interesting for you, or you have always wanted to start your adventure with hardware security, then this talk is for you! This presentation will guide you through the process of designing and testing a CPU backdoor. To make it more interesting, we will focus on the modern x86 processor running regular Linux. During the talk, I’ll briefly revise for you security mechanisms in modern processors, including the most important topics such as ring protection (kernel mode, user mode) and memory virtualization. After that I will guide you through the process of the design of the hardware threat. The practical difficulties will be explained in detail using the proof-of-concept implementation using Qemu x86 CPU emulator. I will show you also how to exploit the threat to leverage the security protection mechanisms of the modern Linux kernel. The aim of this talk is to remind you that the security of computer systems is based on a specific ""symbiosis"" between hardware and software protection mechanisms and attack will most probably also conducted as such combination. Finally, you will learn about the cost and complexity of the prevention mechanism. Consequently, you will see the whole process from the threat injection to the exploitation, which you can repeat yourself! Understanding these attacks plays a critical role in prevention which could be difficult and expensive as it requires special equipment and trained personnel. After this talk, you will have a solid foundation to assess for yourself the controversies surrounding today's hardware security: 5G network or vulnerabilities in x86 processors.

