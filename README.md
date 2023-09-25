FORK FUNCTION:
An existing process can create a new one by calling the fork function .The 
new process created by fork is called the child process. This function is called 
once but returns twice. The only difference in the returns is that the return value in 
the child is 0, whereas the return value in the parent is the process ID of the new 
child. The reason the child's process ID is returned to the parent is that a process 
can have more than one child, and there is no function that allows a process to 
obtain the process IDs of its children. The reason fork returns 0 to the child is that 
a process can have only a single parent, and the child can always call getppid to 
obtain the process ID of its parent. (Process ID 0 is reserved for use by the kernel, 
so it's not possible for 0 to be the process ID of a child.)
Both the child and the parent continue executing with the instruction that follows 
the call to fork. The child is a copy of the parent.

fork();
System call fork() is used to create processes. It takes no arguments and 
returns a process ID. The purpose of fork() is to create a new process, which 
becomes the child process of the caller.
After a new child process is created, both processes will execute the next 
instruction following the fork() system call .This can be done by testing the 
returned value of fork() .
• If fork() returns a negative value, the creation of process was 
unsuccessful. 
• If fork() returns zero(0), then child has created. 
• If fork() returns positive value, which is the process ID of the child process, 
to the parent. 





WAIT:
When a process terminates, either normally or abnormally, the kernel notifies the 
parent by sending the SIGCHLD signal to the parent. Because the termination of 
a child is an asynchronous event it can happen at any time while the parent is 
running this signal is the asynchronous notification from the kernel to the parent. 
The parent can choose to ignore this signal, or it can provide a function that is 
called when the signal occurs: a signal handler. The default action for this signal 
is to be ignored. A process that calls wait() or waitpid() can block, if all of its children 
are still running
• Return immediately with the termination status of a child, if a child has 
terminated and is waiting for its termination status to be fetched . 
• Return immediately with an error, if it doesn't have any child processes. 
• The wait function can block the caller (parent) until a child process 
terminates. If a child has already terminated , the child is called is a zombie, 
otherwise wait returns immediately with that child's status.

Wait()
The wait function can block the caller until a child process terminates. If a child has 
already terminated and is a zombie, wait returns immediately with that child's 
status. Otherwise, it blocks the caller until a child terminates. If the caller blocks 
and has multiple children, wait returns when one terminates.





ORPHAN PROCESS:
An orphan process in unix and unix like operating system, is a computer 
process whose parent process has finished or terminated, through itself remains 
running . A process can become orphaned during remote invocation when the 
client process crashes after making a request to server.
A process can also be orphaned running on the same machine as its parent 
process. In a UNIX-like operating system any orphaned process will be 
immediately adopted by the special “init” process as its parent, it is still called an 
orphan process since the process which originally created no longer exists.





ZOMBIE PROCESS:
A zombie process or defunct process is a process that has completed execution 
but still has an entry in the process table. This entry is still needed to allow the 
process that started the (new zombie) process to read its exit status. The term 
zombie process derives from the common definition of zombie an undead process.
A zombie process is not the same as an orphan process. An orphan process is a 
process that is still executing, but whose parent has died. They do not become 
zombie processes; instead, they are adopted by init (process ID 1), which waits on 
its children .
When a process ends, all of the memory and resources associated with it are 
deallocated so they can be used by other processes. However, the process’s entry 
in the process table remains. The parent can read the child’s exit status by 
executing the wait system call, at which stage the zombie is removed.
