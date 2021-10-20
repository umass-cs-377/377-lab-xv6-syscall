# Syscall Lab

### Purpose

To understand the process of adding and using a syscall in Xv6.

### Objective

Add a syscall to Xv6 that prints the little lad dance to the console when called. 

### Instructions

Most steps have an associated question in Gradescope, so make sure to follow along. The question will be in reference to the same file the step has you editing.

### Step 1

Add the following line to the end of 'syscall.h':
```
#define SYS_littlelad 22
```

### Step 2

In 'syscall.c' at the end of the `static int (*syscalls[])(void)` list on lines 108-130, add the following:
```
[SYS_littlelad] sys_littlelad
```

Still in 'syscall.c', add the following after line 105:
```
extern int sys_littlelad(void);
```

### Step 3

In 'sysproc.c' add the following function:
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

In 'usys.S', add the following line to the end:
```
SYSCALL(littlelad)
```

### Step 5

In 'user.h' add the following line under the function stubs labelled 'system calls':
```
int littlelad(void);
```


### Step 6
In 'proc.c' add the following function:
```
void
littlelad(void)
{
  cprintf("Berries and cream, berries and cream, I'm a little lad who loves berries and cream!\n");
}
```


### Step 7

Lastly, in 'defs.h' add the following in the list of function definitions labelled 'proc.c':
```
void            littlelad(void);
```
