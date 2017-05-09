---
layout: post
title: Kernel mode hooking, good features getting rotten
tags: [interrupt, kernel, protected, security, userland]
comments: true
---

### Disclaimer

_This article should be read with the sole purpose of education. __No users
nor machines must be hurt or damaged. Ethics first. Fun later._

Modern x86 Operating Systems, use **protected mode** to execute
instructions. In protected mode there are 4 different privilege levels, from 0
to 3. They are also referred to as **ring0** \- **ring3**, to indicate the
level of separation between them. 

The highest-level (the least privileged) is
**userland** (ring3) where regular applications run. The lowest-level (the
highest privileged) is kernel mode (ring0) where the kernel or the core of the
operating system runs (basically the code that own the hardware). 

Whenever an
application needs to call the kernel, it uses an **interrupt** to tell to the
kernel which system call to execute. 
This interrupt in Linux x86-32 is
instruction _int $0x80_ and in Linux x86-64 is the instruction _syscall_.

When the CPU takes the interrupt, it switch from ring3 to ring0 and it calls
the _system_call_. 
From this regular and seemingly harmless behavior, nice and
horrible things can be made, if you know what I mean.
[Here](https://github.com/worldofpiggy/C-code/tree/master/kernel_mode_hooking)
is the code that allows to hook a kernel system call and, well, free your
imagination. Happy hacking!
