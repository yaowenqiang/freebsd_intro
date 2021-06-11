# Introduction to the FreeBSD 
## Compare with Linux

### License

+ GNU "Copyleft"
  With GPL 2, must make source available including any of your own work, With GPL 3, source and free use of any patents you own must be provided

> linux  emulation
+ Berkeley "Copycenter"
  Source and patent rights may or may not be provided.

## Distribution Options

+ Desktop 
  + PC-BSD
  + Available at http://www.pcbsd.org/
  + FreeBSD distribution plus 50 most useful desktop applications
+ Server
  + Stock FreeBSD distribution
  + Avaiable at: http://www.freebsd.org/
  + Add services as needed from ports
+ Commercial Support
  + iXsystems
  + http://www.ixsystems.com


## Processes

+ CPU Time
+ Asynchronous events
+ Memory
+ I/O Descriptors

> Processes are the fundamental service provided by UNIX

> JCL

### Optimize use of system calls

> system call
> library call

## Timer

## Processes


Process Resources

+ CPU Time
+ Asynchronous Events
  + timers
  + hardware exceptions
  + external events
  + I/O Events
+ Memory
  + text/data
  + heap(malloc/sbrk)
  + runtiem stack
+ I/O Descriptors
  + file descriptors
  + pipes
  + sockets
  + streams


> BSD Process Structure

### Process versus threads

+ Kthread model
  + one process structure
  + multiple threads
+ rfork model
  + each thread has its own process structure
  + same model as that used by Linux

## Processes Stats

+ runnable
  + states: CAN_RUN|RUNQ|RUNNING
  + in memory or awaiting swapin(flag SWAPPED)
+ sleeping
  + states: SLEEPING|LOCK|IWAIT
  + td_wchan holds sleep 'address'
+ stopped
  + state: STOPPED
  + stopped by job control or tracing
  + returns to sleep (wchan non-zero) or run
+ minor states
  + NEW - being created in fork
  + ZOMBIE - exited, holds exit status for parent


## Scheduling

### Scheduling Classes


Threads are divided into five scheduling classes


Priority | Class | Thread type 
---------| ------| -----------
0-47     | ITHD  | Bottom-haf kernel(interrupt)
48-79    | REALTIME | Real-time user
80-119   | KERN  | Top-half Kernel
120-223  | TIMESHARE | Time-sharing user
224-255  | IDLE   | idle user


Higher values of priority imply lower levels of service
ITHD and KERN classes are managed by he kernel
REALTIME and IDLE classes are managed by user processes
TIMESHARE class management shared by kernel and user processes


### Scheduling Choices

+ Real time
  + processes set specific priorities
  + kernel does not change priorities
+ Interactie scheduler(ULE)
  + processor affinity
  + kernel sets priority based on interactivity score
+ Share scheduler (4BSD)
  + multi-level feedback queues
  + kernel changes priority based on run behavior
+ Idle scheduler
  + administrator set specific priorities
  + kernel does not change priorities



## Asynchronous Events

+ Hardware Exceptions
  + traps
  + memory faults
  + arithmetic exceptions
+ External Events
  + Interrupt
  + Quit
  + Stop
+ I/O Events
  + I/O Completion
  + I/O availability
  + Out=of-band data
+ Timer
  + Real time
  + Process virtual time

## process groups and sessions

+ A session  structure describes:
  + Session leader/controlling process
  + controlling terminal vnode and tty
  + login name
  + reference count
  + session identifier
+ Process group structure, pgrp:
  + process group ID # ps j show pgid
  + list of procs in group
  + reference to session
  + other process group state
+ Processes and process groups can be located by ID via hash tables(using linked hash chains, not indices!)


## Operate jails

Create a group of processes with their own root-administered environment

Jail Rules

+ Permitted
  + running or signalling process withing jail
  + changes to files within jail
  + binding ports to jail's IP addresses
  + accessing raw, divert, or routing sockets on jail's virtual network interfaces
+ Not permitted
  + getting information on processes outside of the jail
  + changing kernel variables
  + mounting or unmounting filesystems
  + modifying physical network interfaces or configurations 
  + rerbooting

# Virtual memory

## virtual memory layout
> 32 bit
+ kernel
  + malloc()'ed memory
  + kernel thread stacks'
  + data
  + text
+ user process
  + argv,envp
  + user stack
  + share memory?
  + heap
  + data
  + text

## Use physical memory and swap space

> set virtual memory limits, different with linux ,.inux has no limits ,
