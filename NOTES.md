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

