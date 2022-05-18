0x16. C - Simple Shell
======================

-   By Julien Barbier
-   Project to be done in teams of 2 people (your team: Ekene Okoli, Esther Ashinedu Uvo

Concepts
--------

*For this project, students are expected to look at these concepts:*

-   [Everything you need to know to start coding your own shell](https://alx-intranet.hbtn.io/concepts/64)
-   [Approaching a Project](https://alx-intranet.hbtn.io/concepts/350)

Background Context
------------------

Write a simple UNIX command interpreter.

![](https://s3.amazonaws.com/intranet-projects-files/holbertonschool-low_level_programming/235/shell.jpeg)

*^ "The Gates of Shell", by [Spencer Cheng](https://alx-intranet.hbtn.io/rltoken/AtYRSM03vJDrko9xHodxFQ "Spencer Cheng"), featuring [Julien Barbier](https://alx-intranet.hbtn.io/rltoken/-ezXgcyfhc8qU1DeUInLUA "Julien Barbier")*

Resources
---------

**Read or watch**:

-   [Unix shell](https://alx-intranet.hbtn.io/rltoken/f0YU9TAhniMXWlSXtb64Yw "Unix shell")
-   [Thompson shell](https://alx-intranet.hbtn.io/rltoken/7LJOp2qP7qHUcsOK2-F3qA "Thompson shell")
-   [Ken Thompson](https://alx-intranet.hbtn.io/rltoken/wTSu31ZP1f7fFTJFgRQC7w "Ken Thompson")
-   **Everything you need to know to start coding your own shell** concept page

**man or help**:

-   `sh` (*Run `sh` as well*)

Learning Objectives
-------------------

At the end of this project, you are expected to be able to [explain to anyone](https://alx-intranet.hbtn.io/rltoken/4mHp8pZKm5sjL4-TEJEKeg "explain to anyone"), **without the help of Google**:

### General

-   Who designed and implemented the original Unix operating system
-   Who wrote the first version of the UNIX shell
-   Who invented the B programming language (the direct predecessor to the C programming language)
-   Who is Ken Thompson
-   How does a shell work
-   What is a pid and a ppid
-   How to manipulate the environment of the current process
-   What is the difference between a function and a system call
-   How to create processes
-   What are the three prototypes of `main`
-   How does the shell use the `PATH` to find the programs
-   How to execute another program with the `execve` system call
-   How to suspend the execution of a process until one of its children terminates
-   What is `EOF` / "end-of-file"?

Requirements
------------

### General

-   Allowed editors: `vi`, `vim`, `emacs`
-   All your files will be compiled on Ubuntu 20.04 LTS using `gcc`, using the options `-Wall -Werror -Wextra -pedantic -std=gnu89`
-   All your files should end with a new line
-   A `README.md` file, at the root of the folder of the project is mandatory
-   Your code should use the `Betty` style. It will be checked using [betty-style.pl](https://github.com/holbertonschool/Betty/blob/master/betty-style.pl "betty-style.pl") and [betty-doc.pl](https://github.com/holbertonschool/Betty/blob/master/betty-doc.pl "betty-doc.pl")
-   Your shell should not have any memory leaks
-   No more than 5 functions per file
-   All your header files should be include guarded
-   Use system calls only when you need to ([why?](https://alx-intranet.hbtn.io/rltoken/EU7B1PTSy14INnZEShpobQ "why?"))

### GitHub

**There should be one project repository per group. If you clone/fork/whatever a project repository with the same name before the second deadline, you risk a 0% score.**

More Info
---------

### Output

-   Unless specified otherwise, your program **must have the exact same output** as `sh` (`/bin/sh`) as well as the exact same error output.
-   The only difference is when you print an error, the name of the program must be equivalent to your `argv[0]` (See below)

Example of error with `sh`:

```
$ echo "qwerty" | /bin/sh
/bin/sh: 1: qwerty: not found
$ echo "qwerty" | /bin/../bin/sh
/bin/../bin/sh: 1: qwerty: not found
$

```

Same error with your program `hsh`:

```
$ echo "qwerty" | ./hsh
./hsh: 1: qwerty: not found
$ echo "qwerty" | ./././hsh
./././hsh: 1: qwerty: not found
$

```

### List of allowed functions and system calls

-   `access` (man 2 access)
-   `chdir` (man 2 chdir)
-   `close` (man 2 close)
-   `closedir` (man 3 closedir)
-   `execve` (man 2 execve)
-   `exit` (man 3 exit)
-   `_exit` (man 2 _exit)
-   `fflush` (man 3 fflush)
-   `fork` (man 2 fork)
-   `free` (man 3 free)
-   `getcwd` (man 3 getcwd)
-   `getline` (man 3 getline)
-   `getpid` (man 2 getpid)
-   `isatty` (man 3 isatty)
-   `kill` (man 2 kill)
-   `malloc` (man 3 malloc)
-   `open` (man 2 open)
-   `opendir` (man 3 opendir)
-   `perror` (man 3 perror)
-   `read` (man 2 read)
-   `readdir` (man 3 readdir)
-   `signal` (man 2 signal)
-   `stat` (__xstat) (man 2 stat)
-   `lstat` (__lxstat) (man 2 lstat)
-   `fstat` (__fxstat) (man 2 fstat)
-   `strtok` (man 3 strtok)
-   `wait` (man 2 wait)
-   `waitpid` (man 2 waitpid)
-   `wait3` (man 2 wait3)
-   `wait4` (man 2 wait4)
-   `write` (man 2 write)

### Compilation

Your shell will be compiled this way:

```
gcc -Wall -Werror -Wextra -pedantic -std=gnu89 *.c -o hsh

```

### Testing

Your shell should work like this in interactive mode:

```
$ ./hsh
($) /bin/ls
hsh main.c shell.c
($)
($) exit
$

```

But also in non-interactive mode:

```
$ echo "/bin/ls" | ./hsh
hsh main.c shell.c test_ls_2
$
$ cat test_ls_2
/bin/ls
/bin/ls
$
$ cat test_ls_2 | ./hsh
hsh main.c shell.c test_ls_2
hsh main.c shell.c test_ls_2
$

```

### Checks

The Checker will be released at the end of the project (1-2 days before the deadline). We **strongly** encourage the entire class to work together to create a suite of checks covering both regular tests and edge cases for each task. See task `8\. Test suite`.

## Authors
* **Ekene Okoli** || [Twitter](https://twitter.com/khennyyofficial)
* **Esther Ashinedu Uvo** || [Twitter](https://twitter.com/)
