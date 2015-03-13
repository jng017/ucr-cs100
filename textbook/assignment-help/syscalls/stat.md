#System calls towards gathering information on files

This file contains information on the system calls needed to gather information on specific files. The `stat` system call and its variants, `fstat` and `lstat` will allow the user to store the properties of a file in a data structure. From there, relevant information can be extracted from that struct using other system calls or functions.

**IMPORTANT:**
These system calls return information in data types and binary values that are ideal for computers, but not for humans, To get the information from the `stat` system call to become readable for human eyes, refer to the system calls tutorial made by past cs100 students below.
* [Obtaining info from processes](./getinfo.md)

##stat:

**includes:** `#include <sys/types.h>` `#include <sys/stat.h>` `#include <unistd.h>`

**declaration:** `int stat(const char*pathname, struct stat *buf);`

**returns:** Error occurs if `-1` is returned; otherwise, a `stat` structure is returned.

[man page](http://linux.die.net/man/2/stat)

##fstat:
**includes:** `#include <sys/types.h>` `#include <sys/stat.h>` `#include <unistd.h>`

**declaration:** `int stat(int fd, struct stat *buf);`

**returns:** Error occurs if `-1` is returned; otherwise, a `stat` structure is returned.

[man page](http://linux.die.net/man/2/stat) 

##lstat:
**includes:** `#include <sys/types.h>` `#include <sys/stat.h>` `#include <unistd.h>`

**declaration:** `int stat(const char*pathname, struct stat *buf);`

**returns:** Error occurs if `-1` is returned; otherwise, a `stat` structure is returned.

[man page](http://linux.die.net/man/2/stat) 

##The stat structure:

The `stat` system call takes in a file name and returns information about that file into a `stat` struct which is passed in as the second argument. From there, it is possible to access information about the file by accessing the struct's attributes. Those attributes are shown below:
```
struct stat {
               dev_t     st_dev;         /* ID of device containing file */
               ino_t     st_ino;         /* inode number */
               mode_t    st_mode;        /* protection */
               nlink_t   st_nlink;       /* number of hard links */
               uid_t     st_uid;         /* user ID of owner */
               gid_t     st_gid;         /* group ID of owner */
               dev_t     st_rdev;        /* device ID (if special file) */
               off_t     st_size;        /* total size, in bytes */
               blksize_t st_blksize;     /* blocksize for filesystem I/O */
               blkcnt_t  st_blocks;      /* number of 512B blocks allocated */

};

```




