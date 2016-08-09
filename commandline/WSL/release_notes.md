---
author: russalex
---

# Release Notes

## Build 14388+
For general Windows information on build 14388 visit the [Windows Blog](https://aka.ms/14388wip). <br/>
To track or report an issue visit our [Github page](https://github.com/Microsoft/BashOnWindows/issues). <br/>
### Fixed
- Fixes to prepare for the Windows 10 Anniversary Update on 8/2
  - More information about WSL in the Anniversary Update can be found on our [blog](https://blogs.msdn.microsoft.com/wsl/)


<br/>
<br/>

## Build 14376
For general Windows information on build 14376 visit the [Windows Blog] (https://blogs.windows.com/windowsexperience/2016/06/28/announcing-windows-10-insider-preview-build-14376-for-pc-and-mobile/). <br/>
To track or report an issue visit our [Github page](https://github.com/Microsoft/BashOnWindows/issues). <br/>
### Fixed
- Removed some instances where apt-get hangs (GH #493)
- Fixed an issue where empty mounts were not handled correctly
- Fixed an issue where ramdisks were not mounted correctly
- Change unix socket accept to support flags (partial GH #451)
- Fixed common network related bluescreen
- Fixed bluescreen when accessing /proc/[pid]/task (GH #523)
- Fixed high CPU utilization for some pty scenarios (GH #488, #504)
- Additional bugfixes and improvements

<br/>
<br/>

## Build 14371
For general Windows information on build 14371 visit the [Windows Blog] (https://blogs.windows.com/windowsexperience/2016/06/22/announcing-windows-10-insider-preview-build-14371-for-pc/). <br/>
To track or report an issue visit our [Github page](https://github.com/Microsoft/BashOnWindows/issues). <br/>
### Fixed
- Corrected timing race with SIGCHLD and wait() when using ptrace
- Corrected some behavior when paths have a trailing /  (GH #432)
- Fixed issue with rename/unlink failing due to open handles to children
- Additional bugfixes and improvements

<br/>
<br/>

##Build 14366
For general Windows information on build 14366 visit the [Windows Blog] (https://blogs.windows.com/windowsexperience/2016/06/14/announcing-windows-10-insider-preview-build-14366-mobile-build-14364/). <br/>
To track or report an issue visit our [Github page](https://github.com/Microsoft/BashOnWindows/issues). <br/>
###Fixed
- Fix in file creation through symlinks
-	Added listxattr for Python (GH 385)
-	Additional bugfixes and improvements

###Syscall Support
-	Below are a list of new or enhanced syscalls that have some implementation in WSL. The syscalls on this list are supported in at least one scenario, but may not have all parameters supported at this time.

`listxattr`<br/>
<br/>

##Build 14361
For general Windows information on build 14361 visit the [Windows Blog](http://aka.ms/wip14361). <br/>
To track or report an issue visit our [Github page](https://github.com/Microsoft/BashOnWindows/issues). <br/>
###Fixed
- DrvFs is now case sensitive when running in Bash on Ubuntu on Windows.
  - Users may case.txt and CASE.TXT on their /mnt/c drives
  - Case sensitivity is only supported within Bash on Ubuntu on Windows. When outside of Bash NTFS will report the files correctly, but unexpected behavior may occur interacting with the files from Windows.
  - The root of each volume (i.e. /mnt/c) is not case sensitive
  - More information on handling these files in Windows can be found [here](https://support.microsoft.com/en-us/kb/100625).
- Greatly enhanced pty / tty support.  Applications like TMUX now supported (GH #40)
- Fixed install issue where user accounts not always created
- Optimized command line arg structure allowing for extremely long argument list. (GH #153)
- Now able to delete and chmod read_only files from DrvFs
- Fixed some instances where the terminal hangs on disconnect (GH #43)
- chmod and chown now work on tty devices
- Allow connection to 0.0.0.0 and :: as localhost (GH #388)
- Sendmsg/recvmsg now handle an IO vector length of >1 (partial GH #376)
- Users can now opt-out of auto-generated hosts file (GH #398)
- Automatically match Linux locale to the NT locale during install (GH #11)
- Added the /proc/sys/vm/swappiness file (GH #306)
- strace now exits correctly
- Allow pipes to be reopened through /proc/self/fd (GH #222)
- Hide directories under %LOCALAPPDATA%\lxss from DrvFs (GH #270)
- Better handling of bash.exe ~.  Commands like “bash ~ -c ls” now supported (GH #467)
- Sockets now notify epoll read available during shutdown (GH #271)
- lxrun /uninstall does a better job of deleting the files and folders
- Corrected ps -f (GH #246)
- Improved support for x11 apps such as xEmacs (GH #481)
- Updated initial thread stack size to match default Ubuntu setting and reporting the size correctly to the get_rlimit syscall (GH #172, #258)
- Improved reporting of pico process image names (e.g., for auditing)
- Implemented /proc/mountinfo for df command
- Fixed symlink error code for child name . and ..
- Additional improvements bugfixes and improvements

###Syscall Support
Below are a list of new or enhanced syscalls that have some implementation in WSL. The syscalls on this list are supported in at least one scenario, but may not have all parameters supported at this time.

`GETTIMER`<br/>
`MKNODAT`<br/>
`RENAMEAT`<br/>
`SENDFILE`<br/>
`SENDFILE64`<br/>
`SYNC_FILE_RANGE`<br/>
<br/>

##Build 14352
For general Windows information on build 14352 visit the [Windows Blog](http://aka.ms/wip14352).<br/>
To track or report an issue visit our [Github page](https://github.com/Microsoft/BashOnWindows/issues). <br/>

###Fixed
- Fixed issue where large files were not downloaded / created correctly.  This should unblock npm and other scenarios (GH #3, GH #313)
- Removed some instances where sockets hang
- Corrected some ptrace errors
- Fixed issue with WSL allowing filenames longer than 255 characters
- Improved support for non-English characters
- Add current Windows timezone data and set as default
- Unique device id’s for each mount point (jre fix – GH #49)
- Correct issue with paths containing “.” and “..”
- Added Fifo support (GH #71)
- Updated format of resolv.conf to match native Ubuntu format
- Some procfs cleanup
- Enabled ping for Administrator consoles (GH #18)
 
###Syscall Support
Below are a list of new or enhanced syscalls that have some implementation in WSL. The syscalls on this list are supported in at least one scenario, but may not have all parameters supported at this time.

`FALLOCATE`<br/>
`EXECVE`<br/>
`LGETXATTR`<br/>
`FGETXATTR`<br/>
<br/>

##Build 14342
For general Windows information on build 14342 the [Windows Blog](http://aka.ms/wip14342). <br/>
To track or report an issue visit our [Github page](https://github.com/Microsoft/BashOnWindows/issues). <br/>
Information on VolFs and DriveFs can be found on the [WSL Blog](https://blogs.msdn.microsoft.com/wsl). <br/>

###Fixed
- Fixed install issue when the Windows user had Unicode characters in the username
- The apt-get update udev workaround in the FAQ is now provided by default on first run
- Enabled symlinks in DriveFs (/mnt/<drive>) directories
- Symlinks now work between DriveFs and VolFs
- Addressed top level path parsing issue: ls .// will now work as expected
- npm install on DriveFs and the -g options are now working
- Fixed issue preventing PHP server from launching
- Updated default environment values, such as $PATH to closer match native Ubuntu
- Added a weekly maintenance task in Windows to update the apt package cache
- Fixed issue with ELF header validation, WSL now supports all Melkor options
- Zsh shell is functional
- Precompiled Go binaries are now supported
- Prompting on Bash.exe first run is now localized correctly
- /proc/meminfo now returns correct information
- Sockets now supported in VFS
- /dev now mounted as tempfs
- Fifo now supported
- Multi-core systems now showing correctly in /proc/cpuinfo
- Additional improvements and error messages downloading during first run
- Syscall improvements and bugfixes. Supported syscall list below.
- Additional bugfixes and improvements

###Known Issues
- Not resolving ‘..’ correctly on DriveFs in some cases

###Syscall Support
Below are a list of new or enhanced syscalls that have some implementation in WSL. The syscalls on this list are supported in at least one scenario, but may not have all parameters supported at this time.

`FCHOWNAT`<br/>
`GETEUID`<br/>
`GETGID`<br/>
`GETRESUID`<br/>
`GETXATTR`<br/>
`PTRACE`<br/>
`SETGID`<br/>
`SETGROUPS`<br/>
`SETHOSTNAME`<br/>
`SETXATTR`<br/>
<br/>

##Build 14332

For general Windows information on build 14332 visit the [Windows Blog](http://aka.ms/wip14332). <br/>
To track or report an issue visit our [Github page](https://github.com/Microsoft/BashOnWindows/issues). <br/>

###Fixed
- Better resolv.conf generation including prioritizing DNS entries
- Issue with moving files and directories between /mnt and non-/mnt drives 
- Tar files can now be created with symlinks
- Added default /run/lock directory on instance creation
- Update /dev/null to return proper stat info
- Additional errors when downloading during first run
- Syscall improvements and bugfixes. Supported syscall list below.
- Additional improvements bugfixes and improvements

###Syscall Support
Below is the new syscall that has some implementation in WSL. The syscall on this list is supported in at least one scenario, but may not have all parameters supported at this time.

`READLINKAT`<br/>
<br/>

## Build 14328

For general Windows information on build 14332 visit the [Windows Blog](http://aka.ms/wip14328). <br/>
To track or report an issue visit our [Github page](https://github.com/Microsoft/BashOnWindows/issues). <br/>

### New Features
* Now support Linux users.  Installing Bash on Ubuntu on Windows will prompt for creation of a Linux user.  For more information, visit http://aka.ms/wslusers
* Hostname is now set to the Windows computer name, no more @localhost
* For more information on build 14328, visit: http://aka.ms/wip14328

### Fixed
* Symlink improvements for non /mnt/<drive> files
    * npm install now works
    * jdk / jre now installable using instructions found [here](http://xubuntugeek.blogspot.com/2012/09/how-to-install-oracle-jdk-7-manually-in.html).
    * known issue: symlinks do not work for Windows mounts.  Functionality will be available in a later build
* top and htop now display
* Additional error messages for some install failures
* Syscall improvements and bugfixes.  Supported syscall list below.
* Additional improvements bugfixes and improvements

### Syscall Support
Below is a list of syscalls that have some implementation in WSL.  Syscalls on this list are supported in at least one scenario, but may not have all parameters supported at this time.

`ACCEPT`<br/>
`ACCEPT4`<br/>
`ACCESS`<br/>
`ALARM`<br/>
`ARCH_PRCTL`<br/>
`BIND`<br/>
`BRK`<br/>
`CAPGET`<br/>
`CAPSET`<br/>
`CHDIR`<br/>
`CHMOD`<br/>
`CHOWN`<br/>
`CLOCK_GETRES`<br/>
`CLOCK_GETTIME`<br/>
`CLOCK_NANOSLEEP`<br/>
`CLONE`<br/>
`CLOSE`<br/>
`CONNECT`<br/>
`CREAT`<br/>
`DUP`<br/>
`DUP2`<br/>
`DUP3`<br/>
`EPOLL_CREATE`<br/>
`EPOLL_CREATE1`<br/>
`EPOLL_CTL`<br/>
`EPOLL_WAIT`<br/>
`EVENTFD`<br/>
`EVENTFD2`<br/>
`EXECVE`<br/>
`EXIT`<br/>
`EXIT_GROUP`<br/>
`FACCESSAT`<br/>
`FADVISE64`<br/>
`FCHDIR`<br/>
`FCHMOD`<br/>
`FCHMODAT`<br/>
`FCHOWN`<br/>
`FCHOWNAT`<br/>
`FCNTL64`<br/>
`FDATASYNC`<br/>
`FLOCK`<br/>
`FORK`<br/>
`FSETXATTR`<br/>
`FSTAT64`<br/>
`FSTATAT64`<br/>
`FSTATFS64`<br/>
`FSYNC`<br/>
`FTRUNCATE`<br/>
`FTRUNCATE64`<br/>
`FUTEX`<br/>
`GETCPU`<br/>
`GETCWD`<br/>
`GETDENTS`<br/>
`GETDENTS64`<br/>
`GETEGID`<br/>
`GETEGID16`<br/>
`GETEUID`<br/>
`GETEUID16`<br/>
`GETGID`<br/>
`GETGID16`<br/>
`GETGROUPS`<br/>
`GETPEERNAME`<br/>
`GETPGID`<br/>
`GETPGRP`<br/>
`GETPID`<br/>
`GETPPID`<br/>
`GETPRIORITY`<br/>
`GETRESGID`<br/>
`GETRESGID16`<br/>
`GETRESUID`<br/>
`GETRESUID16`<br/>
`GETRLIMIT`<br/>
`GETRUSAGE`<br/>
`GETSID`<br/>
`GETSOCKNAME`<br/>
`GETSOCKOPT`<br/>
`GETTID`<br/>
`GETTIMEOFDAY`<br/>
`GETUID`<br/>
`GETUID16`<br/>
`GETXATTR`<br/>
`GET_ROBUST_LIST`<br/>
`GET_THREAD_AREA`<br/>
`INOTIFY_ADD_WATCH`<br/>
`INOTIFY_INIT`<br/>
`INOTIFY_RM_WATCH`<br/>
`IOCTL`<br/>
`IOPRIO_GET`<br/>
`IOPRIO_SET`<br/>
`KEYCTL`<br/>
`KILL`<br/>
`LCHOWN`<br/>
`LINK`<br/>
`LINKAT`<br/>
`LISTEN`<br/>
`LLSEEK`<br/>
`LSEEK`<br/>
`LSTAT64`<br/>
`MADVISE`<br/>
`MKDIR`<br/>
`MKDIRAT`<br/>
`MKNOD`<br/>
`MLOCK`<br/>
`MMAP`<br/>
`MMAP2`<br/>
`MOUNT`<br/>
`MPROTECT`<br/>
`MREMAP`<br/>
`MSYNC`<br/>
`MUNLOCK`<br/>
`MUNMAP`<br/>
`NANOSLEEP`<br/>
`NEWUNAME`<br/>
`OPEN`<br/>
`OPENAT`<br/>
`PAUSE`<br/>
`PERF_EVENT_OPEN`<br/>
`PERSONALITY`<br/>
`PIPE`<br/>
`PIPE2`<br/>
`POLL`<br/>
`PPOLL`<br/>
`PRCTL`<br/>
`PREAD64`<br/>
`PROCESS_VM_READV`<br/>
`PROCESS_VM_WRITEV`<br/>
`PSELECT6`<br/>
`PTRACE`<br/>
`PWRITE64`<br/>
`READ`<br/>
`READLINK`<br/>
`READV`<br/>
`REBOOT`<br/>
`RECV`<br/>
`RECVFROM`<br/>
`RECVMSG`<br/>
`RENAME`<br/>
`RMDIR`<br/>
`RT_SIGACTION`<br/>
`RT_SIGPENDING`<br/>
`RT_SIGPROCMASK`<br/>
`RT_SIGRETURN`<br/>
`RT_SIGSUSPEND`<br/>
`RT_SIGTIMEDWAIT`<br/>
`SCHED_GETAFFINITY`<br/>
`SCHED_GETPARAM`<br/>
`SCHED_GETSCHEDULER`<br/>
`SCHED_GET_PRIORITY_MAX`<br/>
`SCHED_GET_PRIORITY_MIN`<br/>
`SCHED_SETAFFINITY`<br/>
`SCHED_SETPARAM`<br/>
`SCHED_SETSCHEDULER`<br/>
`SCHED_YIELD`<br/>
`SELECT`<br/>
`SEND`<br/>
`SENDMMSG`<br/>
`SENDMSG`<br/>
`SENDTO`<br/>
`SETDOMAINNAME`<br/>
`SETGID`<br/>
`SETGROUPS`<br/>
`SETHOSTNAME`<br/>
`SETITIMER`<br/>
`SETPGID`<br/>
`SETPRIORITY`<br/>
`SETREGID`<br/>
`SETRESGID`<br/>
`SETRESUID`<br/>
`SETREUID`<br/>
`SETRLIMIT`<br/>
`SETSID`<br/>
`SETSOCKOPT`<br/>
`SETTIMEOFDAY`<br/>
`SETUID`<br/>
`SETXATTR`<br/>
`SET_ROBUST_LIST`<br/>
`SET_THREAD_AREA`<br/>
`SET_TID_ADDRESS`<br/>
`SHUTDOWN`<br/>
`SIGACTION`<br/>
`SIGALTSTACK`<br/>
`SIGPENDING`<br/>
`SIGPROCMASK`<br/>
`SIGRETURN`<br/>
`SIGSUSPEND`<br/>
`SOCKET`<br/>
`SOCKETCALL`<br/>
`SOCKETPAIR`<br/>
`SPLICE`<br/>
`STAT64`<br/>
`STATFS64`<br/>
`SYMLINK`<br/>
`SYMLINKAT`<br/>
`SYNC`<br/>
`SYSINFO`<br/>
`TEE`<br/>
`TGKILL`<br/>
`TIME`<br/>
`TIMERFD_CREATE`<br/>
`TIMERFD_GETTIME`<br/>
`TIMERFD_SETTIME`<br/>
`TIMES`<br/>
`TKILL`<br/>
`TRUNCATE`<br/>
`TRUNCATE64`<br/>
`UMASK`<br/>
`UMOUNT`<br/>
`UMOUNT2`<br/>
`UNLINK`<br/>
`UNLINKAT`<br/>
`UNSHARE`<br/>
`UTIME`<br/>
`UTIMENSAT`<br/>
`UTIMES`<br/>
`VFORK`<br/>
`WAIT4`<br/>
`WAITPID`<br/>
`WRITE`<br/>
`WRITEV`<br/>
