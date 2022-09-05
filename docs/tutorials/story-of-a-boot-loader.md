Story Of A Boot Loader
======================

[SEPTEMBER 28,
2018](https://embeddedprograms.wordpress.com/2018/09/28/story-of-a-boot-loader/)
\~
[ADMIN\@EMBEDDEDPROGRAMS.COM](https://embeddedprograms.wordpress.com/author/embeddedprograms/)

*"A bootstrap is a small strap at the back of a leather boot that
enables you to pull the entire boot on."*

Boot-loader's task is to load the kernel into RAM and pass control to
kernel. In computers bootstrap is used to load a program into a computer
using a much smaller initial program to load in the desired program
(which is usually an operating system)

In today's world meaning of boot-loader is more than just loading the
operating system (kernel), it provides options to validate/test the
hardware present on the machine. As well provide ways to debug you
program. Most of the boot-loader support GDB debugging.

Boot-loader program very from hardware to hardware, you should be aware
about the assembly language/ instruction for the target platform.

If we talk about the x86 machines, BIOS is the first program that runs
when machine starts, and later it loads the Windows operating system. If
you ever get a change to enter into the BIOS program, you will get lots
of features like enable/disable the hardware properties.

Now let's talk about the embedded systems, we have mindset that embedded
system have very limited memory. But if we look around we find that's
not valid now a days, we have enough memory, apart from few embedded
systems. So memory is not a constraint, but still we make sure that our
boot-loader program takes minimum time to boot up.

U-boot is quite famous bootloader; it was initially developed by Denx
for PowerPC. Other bootloaders derived from the U-boot are PPCBoot,
RedBoot, Barebox. Barebox is called the U-boot version 2, it takes the
advantage of linux config file system.

#### ARM Boot-loaders:

In arm, boot-loaders are divided into three stages:

1\) **Boot-ROM**: A simple boot-loader, which resides into ROM, and its
duty is to initialize the SRAM and loads the first stage boot-loader
into SRAM. SRAM is also a small memory.

2\) **First stage boot-loader**: A first stage boot-loader runs itself
from SRAM and its primary responsibility is to initialize the DRAM and
loads the secondary boot-loader and pass control to it.

3\) **Second stage boot-loader**: This boot-loader is the full-fledged
boot-loader, which provides different options to debug/run the program.
It does some set of basic initialization again and passes the control to
the kernel.

4\) **Operating System**: Once kernel gets the control, it decompresses
itself and does initializations of all the peripherals. At last you get
the prompt, now you can execute you favorite program.

#### Boot-loader's Initializations Steps:

In brief the following are the generic things that boot-loader does

1\. Disable all interrupts.

2\. Copy any initialized data from ROM to RAM.

3\. Zero the uninitialized data area.

4\. Allocate space for and initialize the stack.

5\. Initialize the processor's stack pointer.

6\. Create and initialize the heap.

7\. Execute the initializers for all global data

8\. Enable interrupts.

9\. Call main loop.

#### Optimizations:

As boot-loader should take minimal time to boot, it must be optimized
for the performance. The following are the things that should be taken
care while writing code for the boot-loader.

· Use inline functions whenever possible? it increases code size but
saves u the overhead of stack push & pop operations

· Code all critical / frequently used code in assembly

· Store frequently used variables in register

· Use global variables it saves you push/pop stack operation during
function call.

· Don't use floating point calculations / variables.

· Enable GCC Optimization.

o -O1 = With this option the resulting executable should be smaller and
faster than with -O0

o -O2 = This option is generally the best choice for deployment of a
program

o -O3 = This option may increase the speed of the resulting executable,
but can also increase its size

o -Os = This option selects optimizations which reduce the size of an
executable.

Refer the below link for the list and comparison of all the boot-loaders
available in the market.

<https://en.wikipedia.org/wiki/Comparison_of_boot_loaders>

#### Conclusion:

It's really crucial decision to choose the right boot-loader for your
platform. Generally the trade-off between features and performance, so
first list all the features required for the platform. Latter choose the
best available options from the list of the boot-loader's available in
the market. If performance is the major concern for you platform, I
suggest write your own piece of code which does the minimum set of
initializations, but it requires lots of time and effort to development.
Best approach is to pick an open source boot-loader from the market, and
customize it as per your needs. Modern boot-loaders like u-boot gives
flexibility to configure the features required as per your needs.

#### **Summary**:

Boot-loader is a program whose primary job is to load the kernel and
pass control to it. Additionally it provides features to test and debug
the present hardware. Arm supports three stage boot-loaders which gives
additional security from the hackers. Primary objective while writing
boot-loader is to make it optimized for performance.

#### **References**:

1\. <http://en.wikipedia.org/wiki/Booting>

2\. <http://searchcio-midmarket.techtarget.com/definition/bootstrap>

3\. <http://www.denx.de/wiki/U-Boot>
