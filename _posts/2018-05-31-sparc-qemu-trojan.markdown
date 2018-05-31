---
layout: post
title:  "Implementing a HW Trojan in QEMU for Sparc architecture"
date:   2018-05-31 10:38:12 +0200
categories: jekyll update
---
This is a short tutorial for implementation of the CPU backdoor with the help of QEMU emulator.
Sources for the implementation are available here : [https://github.com/AdamKostrzewa/qemuSparcTrojan](https://github.com/AdamKostrzewa/qemuSparcTrojan)


Requirements:
* QEMU emulator version 2.12.50 (v2.12.0-rc3-71-g6af2692e86-dirty)
cloned from [git clone git://git.qemu.org/qemu.git](git clone git://git.qemu.org/qemu.git) 
* buildroot-2018.02.1 for cross compilation
cloned from [git clone git://git.buildroot.net/buildroot](git clone git://git.buildroot.net/buildroot) 

You may install qemu sources with :

{% highlight shell %}
wget https://download.qemu.org/qemu-2.12.0.tar.xz
tar xvJf qemu-2.12.0.tar.xz
cd qemu-2.12.0
./configure
make
{% endhighlight %}

All sources were checked on (26-May-2018)
 

Description:

The goal of this project is to present the simple implementation of the CPU backdoor in the Sparc pipeline using the Qemu emulator.
Consequently, the trojan's payload is placed in
The payload of the 


Application notes:

* Clone the repository
* Copy the ui3.vhd to the ~/grlib-gpl-2017.2-b4194/lib/gaisler/leon3v3 (where is ~/grlib-gpl-2017.2-b4194/ is the path of the installation directory)
* Compile and run the library
	Presented tests were conducted with the leon3-minimal (~/grlib-gpl-2017.2-b4194/designs/leon3-minimal)
* Compile and run the exploit.c
 sparc-gaisler-elf-gcc -O0 -g exploit.c -o exploit
 sparc-elf-objcopy -O srec exploit ram.srec 
* run the simulation
 e.g. make vsim-run

If code is executed without the backdoor the exception will be produced due to the illegal instruction RDPSR
as we have not set any handler the simulation will finish abruptly:

{% highlight ruby %}
\# 
\#   b 87878787
\# ** Failure: *** IU in error mode, simulation halted ***
\#    Time: 838105 ns  Iteration: 13  Process: /testbench/iuerr File: testbench.vhd
\# Break in Process iuerr at testbench.vhd line 127
\# Stopped at testbench.vhd line 127 
VSIM 2> quit
{% endhighlight %}
when the backdoor is activated the following output will be produced:

{% highlight ruby %}
\#  
\#  
\#    b 87878787
\#  
\#  
\#    psr f34000e7
{% endhighlight %}

Explanation and comments:
The code is executed on in the barebone mode (only prom.S has been loaded). 
Therefore the processor is running in supervisor mode.
Firstly we switch to the user mode bcc_set_psr(0xf3400027);
Than we set the operands for the backdoor and activate the addition.

{% highlight ruby %}
int a = 87878786;
int b = 1;
b = b + a;
{% endhighlight %}

Finally, we read the psr value with psr = bcc_get_psr();

Execution will follow inifinitely due to the while(1) loop.

If we are still in user mode the exception is raised as RDPSR | WRPSR are privileged instructions.
Consult the SPARC Manual v8 for more details.

