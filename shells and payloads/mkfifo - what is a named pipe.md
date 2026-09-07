named pipe is an operating-system communication mechanism that utilizes the FIFO ordering discipline to preserver the order of the data written to it.

 the named pipe is not it self an algorithm, but an OS object. so the FIFO association is happen because its describes an important behavioral property of the pipe.

like the traditional concept of pipe, a named pipe is one of the methods of inter-process comunnication (IPC)

different from an pipe(I) that just chain datastreams as long as the process exists, the named pipe redirect, remains alive in a special file so it can last beyond the life of the process. in most cases until the system is up.