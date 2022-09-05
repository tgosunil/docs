System Programming Interview Questions
======================================

1.  What is a volatile variable ? What does the compiler do with
    > volatile variables ? Where volatile variables are used ?
2.  Can a pointer be volatile ?
3.  What is constant ?
4.  Can a variable be both volatile and constant ?
5.  Difference between 'const char \*A' and 'char \*const A' ?
6.  What is a void pointer and what is its use ?
7.  What are the preprocessors ?
8.  What are the advantages of macros over constants ?
9.  Is it possible to find the address of a variable of type 'register'
    > ?
10. What is structure padding? Is there any way to tell the compiler to
    > avoid structure padding ?
11. How do you find a loop in a linked list ?
12. Can structures be passed as to the functions by value ?
13. What are the minimum requirements to jump control from assembly
    > program to C program ?
14. What are the different segments in the executable ? Describe
    > individual usage.
15. What is the ELF file format ? Describe its different sections.
16. How will you flash an image to the bare board ?
17. Is it possible to execute code directly from NAND flash (without
    > loading it into RAM) ?
18. What is the difference between a malloc() and a calloc() ?
19. What malloc(0) will return ?
20. How free() knows how much memory needs to be free ?
21. What is big endian and little endian ?
22. What things do you take care of in code to avoid endianness related
    > issues ?
23. Write a program to find the endianness of a machine ?
24. Write a program to convert from big endian to little endian ?
25. Have you used the IPC mechanism ? Define individual pros and cons.
26. What are the different synchronization mechanisms ?
27. Where semaphores are used ?
28. What is the difference between binary semaphore and mutex ?
29. Where spin locks are used apart from the interrupt handler ?
30. Is spin-lock available in uniprocessor system ?
31. What are physical addresses and virtual addresses ? Why do we use
    > virtual addresses ? How will you map a physical address in Linux ?
32. Are you aware of Linux Memory Management ?
33. What is the difference between kmalloc() and vmalloc() ?
34. Is it possible to allocate memory in Stack ? How ?
35. What is a "Flat Memory" model ?
36. What is virtualization ?
37. How will you register an interrupt in Linux ? What will be the
    > return value of the interrupt handler ?
38. What are top-half and bottom-half ?
39. What are the things you care about while writing an interrupt
    > handler ?
40. What is the difference between softirq, tasklet and workqueue ?
41. Describe the interrupt handling mechanism in OS from the point
    > hardware generates an interrupt till its interrupt handler gets
    > called ?
42. What is the difference between an exception and interrupt ?
43. How will you allocate memory in the interrupt handler ?
44. Which posix API is used to create a thread ?
45. What is priority inversion ?
46. What is SMP? How is synchronization done in the SMP system ?
47. What is a system call ? Why is 'asm linkage' used ?
48. How is the file system implemented in Linux OS ?
49. How will you design/write a new BSP in Linux ?
50. What is the difference between char and block drivers?
51. How will you write a driver for a device? Design parameter..?
52. How will you debug your driver ?
53. Have you ever faced cache related issues ? If yes then how will you
    > resolve it ?
54. Write a program to reverse a string.
55. Write a macro to get offset of its variable (i.e.
    > OFFSET\_OF(element, struct\_t))
56. Write a program to count the number of set bits in a 32 bit integer.
57. Write a program to insert a node in a doubly linked list.
58. Write a program to make an address page alignment.
59. Write a program in c which takes a variable number of parameters.
60. Write a program for dynamic allocation of 2D arrays.
