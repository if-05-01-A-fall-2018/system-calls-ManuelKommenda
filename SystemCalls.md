# System Calls Understanding

### fork

fork - create a child process

fork() creates a new process by duplicating the calling process. The new process is a child process from the parent (call) process. Directly after the fork() both processes have the same content (same program code).

fork(void);

### stat

stat - display file or file system status.

Display file or file system status.

    1.  -L, --dereference
             follow links
    2.  -f, --file-system
             display file system status instead of file status
    3.  -c  --format=FORMAT
             use the specified FORMAT instead of the default; output newline after each use of FORMAT
    4.  --printf=FORMAT
             like --format, but interpret backslash escapes, and do not output a mandatory trailing newline; if you want a newline, include \n in FORMAT
    5.  -t, --terse
             print the information in terse form
    6.  --help
            display this help and exit
    7.  --version
             output version information and exit

### kill

kill - terminate a process

The command kill sends the specified signal to the specified processes or process groups. If no signal is specified, the TERM signal is sent.  The default action for this signal is to terminate the process.


The list of processes to be signaled can be a mixture of names and PIDs.

   1. pid    Each pid can be one of four things:

      -  n      where n is larger than 0.  The process with PID n is signaled.
      -  0      All processes in the current process group are signaled.
      -  -1     All processes with a PID larger than 1 are signaled.
      -  -n     where n is larger than 1.  All processes in process group n are signaled.

  2. name   All processes invoked using this name will be signaled.

### mmap

mmap, munmap - map or unmap files or devices into memory

mmap() creates a new mapping in the virtual address space of the calling process. The starting address for the new mapping is specified in addr.

    1. PROT_EXEC  Pages may be executed.
    2. PROT_READ  Pages may be read.
    3. PROT_WRITE Pages may be written.
    4. PROT_NONE  Pages may not be accessed.

### chmod

chmod - change file modes.

chmod changes the file mode bits of each given file according to mode.

### waitpid

waitpid — wait for a child process to stop or terminate

The waitpid() functions shall obtain status information pertaining to one of the caller's child processes. Various options permit status information to be obtained for child processes that have terminated or stopped.

The waitpid() function shall be equivalent to wait() if the pid argument is (pid_t)−1 and the options argument is 0. The pid argument specifies a set of child processes for which status is requested.

    1. If pid is equal to (pid_t)−1, status is requested for any child process.

    2. If pid is greater than 0, it specifies the process ID of a single child process for   
       which status is requested.
    3. If pid is 0, status is requested for any child process whose
       process group ID is equal to that of the calling process.
    4.  If pid is less than −1, status is requested for any child process whose process
        group ID is equal to the absolute value of pid.


# System Calls Fail

1. fork
    - ENOSYS fork() is not supported on this platform  (for example, hardware without a
      Memory-Management Unit).
2. exec
    - E2BIG The total number of bytes in the environment and argument list is too large.
3. unlinkS
    - ENOTDIR A component used as a directory in pathname is not, in fact, a directory.
4. read
    - EFAULT The buffer is outside of your accessible address space.
5. mount
    - System error If mount returns the value 2 its a system error(out of memory, can not fork).
6. chmod
    - ENOENT The named file does not exist.
7. kill
    - EPERM The process does not have permission to sent the signal to any receiving process.

# Trap

A trap instruction is performed to switch from user mode to kernel mode. It is an exception in a user process.
It is caused by division by zero or invalid memory access. It's also the usual way to invoke a kernel routine (a system call) because those run with a higher priority than user code.
