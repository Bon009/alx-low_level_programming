C File Input/Output

file descriptors can refer to any Unix file type named in a file system. As well as regular files, this includes directories, block and character devices (also called "special files"), Unix domain sockets, and named pipes. File descriptors can also refer to other objects that do not normally exist in the file system, such as anonymous pipes and network sockets.

The FILE data structure in the C standard I/O library usually includes a low level file descriptor for the object in question on Unix-like systems. The overall data structure provides additional abstraction and is instead known as a file handle.

Operations on file descriptors
The following lists typical operations on file descriptors on modern Unix-like systems. Most of these functions are declared in the <unistd.h> header, but some are in the <fcntl.h> header instead.

Creating file descriptors
open()
creat()[5]
socket()
accept()
socketpair()
pipe()
epoll_create() (Linux)
signalfd() (Linux)
eventfd() (Linux)
timerfd_create() (Linux)
memfd_create() (Linux)
userfaultfd() (Linux)
fanotify_init() (Linux)
inotify_init() (Linux)
clone() (with flag CLONE_PIDFD, Linux)
pidfd_open() (Linux)
open_by_handle_at() (Linux)
Deriving file descriptors
dirfd()
fileno()
Operations on a single file descriptor
read(), write()
readv(), writev()
pread(), pwrite()
recv(), send()
recvfrom(), sendto()
recvmsg(), sendmsg() (also used for sending FDs to other processes over a Unix domain socket)
recvmmsg(), sendmmsg()
lseek(), llseek()
fstat()
fstatvfs()
fchmod()
fchown()
ftruncate()
fsync()
fdatasync()
fdopendir()
fgetxattr(), fsetxattr() (Linux)
flistxattr(), fremovexattr() (Linux)
statx (Linux)
setns (Linux)
vmsplice() (Linux)
pidfd_send_signal() (Linux)
waitid() (with P_PIDFD ID type, Linux)
fdopen() (stdio function:converts file descriptor to FILE*)
dprintf() (stdio function: prints to file descriptor)
Operations on multiple file descriptors
select(), pselect()
poll(), ppoll()
epoll_wait(), epoll_pwait(), epoll_pwait2() (Linux, takes a single epoll filedescriptor to wait on many other file descriptors)
epoll_ctl() (for Linux)
kqueue() (for BSD-based systems).
sendfile()
splice(), tee() (for Linux)
copy_file_range() (for Linux)
close_range() (for Linux)[6]
Operations on the file descriptor table
The fcntl() function is used to perform various operations on a file descriptor, depending on the command argument passed to it. There are commands to get and set attributes associated with a file descriptor, including F_GETFD, F_SETFD, F_GETFL and F_SETFL.

close()
closefrom() (BSD and Solaris only; deletes all file descriptors greater than or equal to specified number)
dup() (duplicates an existing file descriptor guaranteeing to be the lowest number available file descriptor)
dup2(), dup3() (Close fd1 if necessary, and make file descriptor fd1 point to the open file of fd2)
fcntl (F_DUPFD)
Operations that modify process state
fchdir() (sets the process's current working directory based on a directory file descriptor)
mmap() (maps ranges of a file into the process's address space)
File locking
flock()
fcntl() (F_GETLK, F_SETLK and F_SETLKW)
lockf()
Sockets
See also: Berkeley sockets
connect()
bind()
listen()
accept() (creates a new file descriptor for an incoming connection)
getsockname()
getpeername()
getsockopt()
setsockopt()
shutdown() (shuts down one or both halves of a full duplex connection)
Miscellaneous
ioctl() (a large collection of miscellaneous operations on a single file descriptor, often associated with a device)
