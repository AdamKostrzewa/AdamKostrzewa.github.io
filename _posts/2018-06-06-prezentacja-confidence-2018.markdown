---
layout: post
title:  "Presentation from Confidence 2018 - Who and why should fear HW trojans?"
date:   2018-06-06 08:38:12 +0200
categories: jekyll update
---
Below you may find my presentation from the Confidence 2018.
Feel free to contact me if you have any questions or doubts 
PDF for download: [Downlad](/download/hw_trojan_confidence.pdf) 

<iframe src="https://drive.google.com/file/d/1JJSzVqXpQqxiF6qqSfLD9DiNOvKGRYMq/preview" width="1000" height="580"></iframe>


Abstract:
Can we trust our processors, routers and other electronic IP components? 
This important question is often left unanswered. Due to the high production complexity and costs of very-large-scale integration (VLSI) 
resulting from contemporary transistor designs, the majority of regular users have little to no choice when selecting hardware 
components and even lower a possibility of validating them. Consequently, many of us are forced to depend on the honesty of big corporations 
and the assumption that if we apply a commonly used component from a known provider sooner or later someone will find such a threat for us. 
However, this does not negate the technical feasibility of hardware attacks, proved by research results, neither confirms that our hardware is 
thoroughly tested e.g. Meltdown and Spectre bugs in Intel CPUs. Moreover, recent scandals, for instance Snowden’s affair, has shown that there are 
organizations and institutions capable of enormous efforts to compromise the security. The goal of the presentation is to familiarize the audience 
with current research results on so-called ‘hardware trojan’, understood as intentional manipulations of integrated circuits (ICs) 
that weaken or compromise the security of the systems. Besides theoretical background, author presents case studies of exemplary attacks,
 which can be directed against CPUs as well as against special ICs in network routers. The dissemination is done through a systematic 
 analysis of steps leading towards the creation of such circuits. Firstly, the requirements will be considered: where and for what purpose 
 hardware vulnerabilities could be placed in products. This includes an evaluation of the possible advantages and disadvantages (as well as 
 similarities and differences) that such solutions have when compared to the known software counterparts. Next, the discussion proceeds with a 
 part addressing technical aspects: how and when, in the process of the VLSI circuit design, a possible hardware threat could be implemented 
 by the manufacturer. Here, different production methods and abstraction layers are discussed e.g. HDL languages, RTL design, chip layout or even 
 fabrication in silicone. This evaluation is supported by the detailed case studies. For demonstration purposes, the implementation of a simple CPU 
 backdoor in the Leon3 processor is considered including a brief overview of the hardware mechanisms (e.g. ring protection) forming a security 
 foundation in most of existing systems. Additionally, the methods used to weaken encryption mechanisms which are becoming the backbone of the 
 complex security solutions are proposed. The final part of the presentation concentrates on the verification and commercial aspects of hardware 
 vulnerabilities. This includes answering the following questions: how difficult is the detection of malicious circuits in contemporary designs? 
 If this happens, what are possible consequences for the “malicious” manufacturers and how could they be avoided. The aim of this talk is 
 to raise the audience’s awareness on the fact that the introduction of 'trojan horses' into the commercially available integrated circuit
 is technically feasible and proven by publications, practical works and press reports. Moreover, the prevention is difficult and 
 expensive requiring specialized equipment and dedicated personnel. Therefore, hardware tests and validation should become the permanent
 parts of corporate and national security policies.


