# From program to executable

Typically **programs** are executed by users and managed by an
_operating system_. _Operating systems_ are themselves a program that originates
from **source code**. _Source code_ typically refers to programs described in a
**high-level language**.  This is then processed into an **assembly lanugage**
and then a **machine code/language** representation, resulting in an executable
file that may be loaded into memory by an operating system.

Code in a _high-level language_ is **compiled** and then **assembled** into
**object files** described in a _machine language_. At this stage it is not yet
_executable_. **Subroutines** within object files are **linked** together so
that they will point towards the beginning section of an object file where the
subroutine is described. **Shared object files/libraries** like a `.dll` or a
`.so` file can either be **statically linked** for inclusion within the
resulting _executable_, or **dynamically linked** at _run-time_ so that the
operating system's **dynamic linker/loader** may link with those
_shared libraries_ residing in _persistent storage_. After being _linked_,
the end executable may now be **loaded** into memory by the operating system.

In the case of **Linux ELF** files, they are _loaded_ into memory and scheduled
onto a thread for execution by the kernel.
The _ELF executable_ can ask the Linux kernel for further interpretation using
the ELF's INTERP(reter) header, which can hold a value similar to
`ld-linux-<arch>.so`, the **run-time link editor** (rtld). The _rtld_ is passed
a pointer to the _ELF executable_ in memory and proesses the _dynamic section_;
linking any requested _shared libraries_ to those in _persistent storage_.

In a nutshell: code can **compile** _source code_ into _assembly code_,
**assemble** that into _object files_ as _machine code_, **link** it with other
_object files_, **load** the resulting _executable_ into memory and
**dynamically-link** _subroutines_ at _run-time_ with _shared libraries_ that
are either already loaded in memory or soon to be from _persistent storage_.

(further)  
[https://www.youtube.com/watch?v=N2y6csonII4] \(Compiling, assembling & linking)  
[https://www.cs.fsu.edu/~baker/opsys/notes/linking.html] \(Linking & loading)  
[https://www.youtube.com/watch?v=lWVQsld8hMI] \(Dynamic loading & linking)  
[https://eli.thegreenplace.net/2012/08/13/how-statically-linked-programs-run-on-linux]
\(How statically linked programs run on Linux)  
[https://stackoverflow.com/questions/8352535/how-does-kernel-get-an-executable-binary-file-running-under-linux]
\(Explains how an ELF gets scheduled onto a thread, starting from the kernel's exec()
system call)  
[https://www.cs.virginia.edu/~dww4s/articles/ld_linux.html] \(Understanding
ld-linux.so, the _run-time link editor_)  
[https://en.wikipedia.org/wiki/Executable_and_Linkable_Format] \(An executable
file format used by Unix and Unix-like systems)

* Determine a _dynamically-linked_ ELF file, and read the _dynamic section_.
  You can use `readlink -d <path-to-ELF-file>`.  
* You should see that the filenames of _shared libraries_ are stored as values.
These values are also associated with a type, which in these cases are of the
type `(NEEDED)`. The _rtld_ will search these filenames in the
_shared library path_ in _persistent storage_ and link it to associated
_subroutines_ in the ELF.

(insight)  
This is a very dense explanation of the process from program to executable. The
further reading material above is invaluable in helping me understand this
process.  
The QEMU hypervisor is useful if you wish to run executables for another
processor architecture. You could study the process in which
_high-level language_ code can be _compiled_ and _assembled_ for a target
architecture differing that of the host machine, a process named
**cross-compiling**.
