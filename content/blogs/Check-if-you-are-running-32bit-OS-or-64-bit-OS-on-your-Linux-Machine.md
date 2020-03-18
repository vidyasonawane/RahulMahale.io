+++
date = "2013-12-10"
title = "Check if you are running 32bit OS or 64 bit OS on your Linux Machine"
tags = ["Linux"]
categories = ["technical blogs"]
+++

Hi, Linux Users

I will elaborate some basic tricks to know your CPU configuration on your Linux System. Many times I have come across a unique question from Linux Users that how should I know that I am using 32 bit CPU/OS or 64 bit CPU/OS? Definitely, I am here to tell you answer of this question but before that, we have to understand some points they are.

1. We can run 32 bit operating system on 64 bit CPU.

2. We can run 64 bit operating system on 64 bit CPU.

3. We cannot run 64 bit operating system on 64 bit CPU.

4. We can run 32 bit operating system on 32 bit CPU.

Once we are clear with these points now we are ready to check of our CPU is 32 bit or 64 bit.

**How to check if CPU is 64 bit supported or not basically there are two ways**

**Method I**

use lscpu command to check if it supports multiple CPU operation modes(either 16, 32 or 64 bit mode).

![blog1](/images/blog.png)

Fig.1 lscpu command

as a normal/root user execute below command

`lscpu | grep op-mode`

Sample output on a 32-bit processor

![blog2](/images/blog_2.png)

Fig.2 Using lscpu with grep

If you observe the first output will say that your CPU supports both 32-bit as well as 64 bit operating systems. This indicates that its 64-bit processor from our above 4 rules. But in the second machine, it says only 32-bit CPU mode which indicates its a 32 bit processor.

**Method II**

Use proc file system file CPU info to get the processor type.

`grep -w lm /proc/cpuinfo`

Sample output on a 32-bit processor when searching for lm(long mode) bit is set or not

![blog3](/images/blog_3.png)

Fig.3 Checking for long mode

If you don't get any output that indicates its not a 64 bit processor.

**How to check if my Operating system is a 64-bit or 32-bit?**

Before knowing about this you should know about i386, i486 etc naming convention.

**What is the difference between i386, i486, i586, and i686 OS?**

They are the names given by the software industry to some softwares for different Intel architectures. If we say i386, its Intel 80386 processor, also known as the i386, or just 386, was a 32-bit microprocessor introduced by Intel in 1985. If I say i486 it is an Intel 80486, i586 it is a 80586 and i686 its a 80686 processor. In short, they are called as x86 family which are of 32 bit processor. And for 64 bit OS, you will get x86_64.

Option 1: check with uname command if your OS is 32 bit or 64 bit.

`uname -m`

![blog4](/images/blog_4.png)

Fig.4 Checking Architecture with uname

`uname -p`

![blog5](/images/blog_5.png)

Fig.5Checking Architecture with uname

Option 2: Check with lscpu command as below.

`lscpu | grep -i arch`

![blog6](/images/blog_6.png)

Fig.6 Checking Architecture with lscpu command

Option 3: Check with getconf command as shown below

`getconf LONG_BIT`

![blog7](/images/blog_7.png)

Fig.7 Checking CPU configuration in Bits

Sample output for 32 bit OS

Please let us know if you know any other way to get OS and Processor processing bit details.