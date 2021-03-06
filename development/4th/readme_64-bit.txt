If you're using 64-bit processor - which nowadays is quite common - you can
compile 4th as 64-bit compiler. To do this, just delete patch #02 before
compilation. But read the following excerpt from original 4th docs first:


25.7 <sec:64-bit-platforms>64-bit platforms

Although 4tH will work perfectly well on a 64-bit platform there 
are some disadvantages:

• HX files generated by this compiler are not portable to 32-bit 
  platforms

• Some 4tH library files may not work properly without some 
  modifications.

A quick fix is to change the size of a cell to a four byte 
datatype. The following procedure will usually work. Open 4th.h 
and change these lines:

#define CELL_MIN LONG_MIN

#define CELL_MAX LONG_MAX

  

typedef long cell;

To this:

#define CELL_MIN INT_MIN

#define CELL_MAX INT_MAX

  

typedef int cell;

Save 4th.h and compile as described in the previous sections. If 
you want a full 64-bit 4tH compiler, be aware that:

• You cannot compile 4tH as a shared library

• You have to regenerate the include files manually, unless 
  you're working with Linux.

Linux automatically recreates the include files each time you 
perform a compile. If you're working with a GNU toolset, you may 
try the Linux Makefile. If that doesn't work or isn't an option 
in your particular situation you'll have to perform the procedure 
listed in section [sec:Regenerating-the-include]. 
