---
layout: post
title:  "[ENG] Test Implementation of a Simple Backdoor in Leon3 iu3 unit"
date:   2018-05-28 14:38:12 +0200
categories: jekyll update
---
This is a short tutorial for implementation of the CPU backdoor in the Leon3 processor.
Sources for the implementation are available here : [https://github.com/AdamKostrzewa/Leon3Backdoor](https://github.com/AdamKostrzewa/Leon3Backdoor)


Requirements:
* GRLIB version: grlib-gpl-2017.2-b4194 
available [http://www.gaisler.com/products/grlib/grlib-gpl-2017.2-b4194.tar.gz](http://www.gaisler.com/products/grlib/grlib-gpl-2017.2-b4194.tar.gz) 
* BCC2 version : Bare-C Cross-Compiler System for LEON2/3/4 GCC 4.9.4 and LLVM/Clang 4.0.0
available [http://www.gaisler.com/index.php/downloads/compilers](http://www.gaisler.com/index.php/downloads/compilers)
* LEON Linux 3.10 
available [http://www.gaisler.com/index.php/downloads/linux](http://www.gaisler.com/index.php/downloads/linux)

Documentation:
* GRLIB User's Manual
* GRLIB IP Cores Manual	
* LEON/GRLIB Configuration Guide
available [http://www.gaisler.com/index.php/downloads/leongrlib](http://www.gaisler.com/index.php/downloads/leongrlib)
* BCC 2 Manual [http://www.gaisler.com/doc/bcc2.pdf](http://www.gaisler.com/doc/bcc2.pdf)

All sources were checked on (08-Aug-2017)


Description:

The goal of this project is to present the simple implementation of the CPU backdoor in the LEON3 pipeline.
The implementation has followed in the ui3.vhd
Activation is done through execution of the ADD instruction with operands (arbitrary) resulting in 87878787


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

