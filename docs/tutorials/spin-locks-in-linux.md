Spin Locks in Linux
===================

[SEPTEMBER 28,
2018](https://embeddedprograms.wordpress.com/2018/09/28/spin-locks-in-linux/)
\~
[ADMIN\@EMBEDDEDPROGRAMS.COM](https://embeddedprograms.wordpress.com/author/embeddedprograms/)

A spinlock is a mutual exclusion device that can have only two values:
"locked" and "unlocked." It is usually implemented as a single bit in an
integer value. Code wishing to take out a particular lock tests the
relevant bit. If the lock is available, the "locked" bit is set and the
code continues into the critical section. If, instead, the lock has been
taken by somebody else, the code goes into a tight loop where it
repeatedly checks the lock until it becomes available. This loop is the
"spin" part of a spinlock.

Any time kernel code holds a spinlock, preemption is disabled on the
relevant processor. Even uni-processor systems must disable preemption
in this way to avoid race conditions.

Below are the variants of spin locks:

-----------------------------------------------------------------------------------------------------------------------------------------

spin\_lock() --- this acquires the spin lock, disables the preemption,
but interrupts are enabled.

--- disables preemption on local CPU

--- acquire spin lock

Usage: This is used when we do not share the critical section with
interrupt handlers (i.e. only in process context).

-----------------------------------------------------------------------------------------------------------------------------------------

spin\_lock\_irq() --- this acquires the spin lock after disabling the
preemption & interrupts on local CPU

--- disable interrupt on local CPU

--- disables preemption on local CPU

--- acquire spin lock

Usage: This is used when we share the critical section with Interrupt
Service Routine.

-----------------------------------------------------------------------------------------------------------------------------------------

spin\_lock\_irqsave() --- same as spin\_lock\_irq() but saves the CPSR
register in a local variable, so that we can restore it later on.

--- save the CPSR into local variable (i.e. flag)

--- disable interrupt on local CPU

--- disables preemption on local CPU

--- acquire spin lock

Usage: This again is used when we share critical section with Interrupt
Service Routine

-----------------------------------------------------------------------------------------------------------------------------------------

spin\_lock\_bh() --- disables software interrupts before taking the
lock, but leaves hardware interrupts enabled.

--- disable bottom-half on local CPU

--- disables preemption on local CPU

--- acquire spin lock

Usage: This is used when we share the critical section with bottom half
