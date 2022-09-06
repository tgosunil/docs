What makes a real RTOS?
=======================

SEPTEMBER 28, 2018 ~ SUNIL KUMAR

Definition of RTOS:

RTOS stands for *Real Time Operating System.*

The real definition of RTOS is:

*"RTOS is an operating system which perform the task in given scheduled
time"*

In other words

"*RTOS schedules the task in definite time*"

Earlier RTOS is requirement in Medical industry, Military & Aerospace
industry, but in today's world RTOS becomes the requirement for consumer
industry as well.

Types of RTOS:

RTOS is further divided into two categories

-   Hard Real Time Operating System (RTOS)

-   Soft Real Time Operating System (RTOS)

#### Hard Real Time Operating System:

It's clear from the name Hard-RTOS schedules the task with more
accuracy; slight deviation from the schedule is not acceptable. System
failure will occur if you miss the deadline.

#### Soft Real Time Operating System:

On the other hand Soft-RTOS provides the flexibility, it can deviate
from the schedule. So it's not recommended for crucial application where
life threat is there.

Scheduler plays a crucial role when RTOS comes into picture; its prime
responsibility is to schedule the entire task in defined time. Scheduler
must be efficient enough schedule each task in predefined time; the key
rule here is scheduler should not have any indefinite parameters.
Indefinite parameters make scheduler difficult to calculate the accurate
time to execute the process, and the system to deviate from the
scheduled time.

### RTOS Criteria:

The following are the parameters that make RTOS to deviate from the
schedule

-   Context Switching time

-   Interrupt latencies

#### Context Switching time

Context-switching time is the time taken by the scheduler to execute the
next process in the scheduling queue. Context switching may occur due to
timeout occurs if Round Robin scheduling, higher priority process comes,
and if interrupt comes from the hardware. During context switching the
scheduler saves the current set of registers into the memory (generally
stack) and loads the next process context from memory. Scheduler itself
takes few cycles to change the context, this time should be minimal. In
case if not possible to minimize the context-switching time, make it
definite. If context- switching time is indefinite, may result in
deviate you operating system from RTOS concept.

#### Interrupt latencies

Second parameter is Interrupt latency, it's the time between the when
hardware generate an interrupt and corresponding hardware interrupt
handler first line gets executed. So operating system itself takes some
time to identify from which device the interrupt has come, and call the
registered interrupt handler for the hardware. Again this time should be
DEFINITE and optimized.

### RTOS Operating Systems:

LynxOS, QNX, VxWorks, RT Linux, Windows CE are famous RTOS in the
market.

### Further Reading:

1\. <http://en.wikipedia.org/wiki/RTOS>

2\. <http://www.qnx.com/developers/articles/article_298_1.html>

3\.
[http://www.barrgroup.com/Embedded-Systems/How-To/RTOS-Selectio](http://www.barrgroup.com/Embedded-Systems/How-To/RTOS-Selection)
