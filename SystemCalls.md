# System Calls

### fork

fork() creates a new process by duplicating the calling process. The new process is a child process from the parent (call) process. Directly after the fork() both processes have the same content.

fork(void);

### stat

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

The command kill sends the specified signal to the specified processes or process groups. If no signal is specified, the TERM signal is sent.  The default action for this signal is to terminate the process.


The list of processes to be signaled can be a mixture of names and PIDs.

   1. pid    Each pid can be one of four things:

      -  n      where n is larger than 0.  The process with PID n is signaled.
      -  0      All processes in the current process group are signaled.
      -  -1     All processes with a PID larger than 1 are signaled.
      -  -n     where n is larger than 1.  All processes in process group n are signaled.

  2. name   All processes invoked using this name will be signaled.

### mmap

mmap() creates a new mapping in the virtual address space of the calling process.
