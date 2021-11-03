# COMPSCI 377 LAB: Syscall Lab

## Purpose
This lab will teach you how to implement a simple system call in the xv6 operating system. Recall, a system call or a `syscall` is how user programs call upon the OS to perform a privileged task. While an actual `syscall` could be complicated, we will simply create a `syscall` that prints a message to the screen. 

Please submit your answers to this lab on Gradescope. All answers are due by the time specified on Gradescope. The TA present in your lab will do a brief explanation of the various parts of this lab, but you are expected to answer all questions by yourself. Please raise your hand if you have any questions during the lab section – TAs will be notified you are asking a question. Questions and Parts have a number of points marked next to them to signify their weight in this lab’s final grade. Labs are weighted equally, regardless of their total points.

## Createing a Syscall

### Step 1

Add the following line to the end of `syscall.h`:
```
#define SYS_littlelad 22
```

### Step 2

In `syscall.c` at the end of the `static int (*syscalls[])(void)` list on lines 108-130, add the following:
```
[SYS_littlelad] sys_littlelad
```

Still in `syscall.c`, add the following after line 105:
```
extern int sys_littlelad(void);
```

### Step 3

In `sysproc.c` add the following function:
```
//does the little lad dance
int
sys_littlelad(void)
{
  littlelad();
  return 0;
}
```


### Step 4

In `usys.S`, add the following line to the end:
```
SYSCALL(littlelad)
```

### Step 5

In `user.h` add the following line under the function stubs labelled `\\system calls`:
```
int littlelad(void);
```


### Step 6
In `proc.c` add the following function:
```
void
littlelad(void)
{
  cprintf("Berries and cream, berries and cream, I'm a little lad who loves berries and cream!\n");
}
```


### Step 7

Lastly, in `defs.h` add the following in the list of function definitions labelled 'proc.c':
```
void            littlelad(void);
```
