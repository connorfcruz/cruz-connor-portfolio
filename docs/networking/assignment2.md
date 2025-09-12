# Command Line Interface

## Project Overview

**Problem Statement:**

In some cases, as well as in the past, having a graphical user interface to interact with a computer either took up very many resources or was simply not available. Thus, this activity teaches students how to navigate and use a command line interface, performing actions such as creating files, moving files, and changing the working directory.

**Objectives:**

- Know what a virtual machine does, as well as applications
- Know how to use a Linux (specifically Ubuntu) virtual machine and deal with the Linux terminal
- Learn basic commands (e.g. pwd and cd) to move through directories and understand absolute vs. relative paths
- Learn how to make, delete, move, copy, and edit files via terminal commands

**Success Criteria:**

Complete several activities, such as "House Sitting Adventure," to demonstrate mastery of command line navigation in the Ubuntu virtual machine.

## Design and Planning

### Due Dates and Planning

INSERT

### Map The Maze (Part 1)

**Useful Definitions/Examples**

| Term | Definition | Example |
| :-------: | :------: | :-------: |
| Root Directory | The highest directory in the file system from which everything branches | "C:\" for PC, "/" for Mac |
| Folder/Directory | Organizes files or other folders | "Desktop" in the home directory |
| File | Object which stores data; has a name and (usually) an extension | Text documents |
| Path | Shows location of a file/folder in the file system; represents the address of a file | "~/Desktop/notes.txt" |
| Absolute Path | The entire address of a file/folder, starting with the root directory | "/Users/Cruz/Music/song.mp3" |
| Relative Path | The location of a file relative to the working directory | "essay.docx" if the working directory has that file |

**File System Tree Activity**

In this activity, students created an example diagram displaying how directories and files are organized and interact with each other by making a file system tree.

Initially, students were tasked to create a top-down diagram starting from the root directory with:
- A home directory
- Three subfolders
- At least two sample files

Here is the diagram:

INSERT DIAGRAM AAAAAAA

Afterwards, that diagram was used to create a text version of the file system tree made previously.

This is the text diagram:

```
/
|_Connor
| |-Downloads
| | |-SoftwareDiagram.jpg
| | |_TheTechInside.mp3
|-Desktop
| |-BinarySearch.java
| |_people-100.csv
|_Documents
  |-LitEssay.docx
  |_CruzDiatomics.xslx
```

**Command Definitions**

| Term | Definition |
| :-------: | :-----------: |
| pwd | Prints the full path of the working directory |
| ls | Lists files/subfolders in the working directory |
| cd | Changes the working directory |
| mkdir | Makes a directory in the working directory |
| touch | Creates an empty file |
| cp | Duplicates a file or directory |
| mv | Moves a file or directory OR renames a file/directory |
| open | Opens a file/directory |
| rm | Removes a file; **CANNOT BE UNDONE** |

**Mac File System Tree**

With the knowledge of basic terminal commands, students were also tasked to create example directories and files in their Mac computers, then navigate through them, doing as follows:
- Create a directory in home called "Practice"
- Make three folders in Practice: Docs, Photos, and Music
- Create a file named "notes.txt" in Docs
- Move notes.txt into Music
- Change the working directory to Music, and print the working directory

These tasks were accomplished using knowledge of the following commands:

- *cd* to change directories
- *mkdir* to create a folder
- *touch* to create a file
- *mv* to move a file
- *pwd* to print the working directory

The final tree structure after this process is:

```
/
|_Users
  |_26cruzc
    |_Practice
      |-Docs
      |-Photos
      |_Music
        |_notes.txt
```

When printing the working directory via 'pwd', this path was obtained: `/Users/26cruzc/Practice/Music`

This matched the path which was obtained through Finder, so it was confirmed that 'pwd' returned the correct working directory.

## Technical Development

### Map The Maze (Part 2)

Using the commands learned during *Map The Maze (Part 1)*, they were similarly applied to the terminal of a Linux virtual machine running on Ubuntu. This activity also entailed linking a directory in the host system to the virtual machine and moving files between them.

```bash
ubuntu@ubuntu:~$ pwd
/home/ubuntu
```

```bash
ubuntu@ubuntu:~$ cd Documents
ubuntu@ubuntu:~/Documents$ pwd
/home/ubuntu/Documents
```

```bash
ubuntu@ubuntu:~/Documents$ mkdir MazeGame
ubuntu@ubuntu:~/Documents$ ls
MazeGame
```

```bash
ubuntu@ubuntu:~/Documents$ cd MazeGame
ubuntu@ubuntu:~/Documents/MazeGame$ touch clue1.txt clue2.txt clue3.txt
ubuntu@ubuntu:~/Documents/MazeGame$ ls
clue1.txt clue2.txt clue3.txt
```

```bash
ubuntu@ubuntu:~/Documents/MazeGame$ nano clue1.txt
```

INSERT NANO OUTPUT

```bash
ubuntu@ubuntu:~/Documents/MazeGame$ sudo cp clue1.txt ~/hostshare
[sudo] password for ubuntu:
ubuntu@ubuntu:~/Documents/MazeGame$ ls ~/hostshare
clue1.txt
```

To copy a file from the Mac to MazeGame, the 'Shared Directory' value in the UTM had to be changed. For the purposes of this assignment, the 'Desktop' folder in the host system was chosen.

After restarting the VM, it was then required to link ~/hostshare and the shared directory (Desktop) via the following command:

```bash
ubuntu@ubuntu:~$ sudo mount -t davfs http://127.0.0.1:9843/ ~/hostshare/
```

```bash
ubuntu@ubuntu:~$ cd hostshare
ubuntu@ubuntu:~/hostshare$ ls
'Screenshot 2025-09-05 at 2.23.11 PM.png'
ubuntu@ubuntu:~/hostshare$ mv 'Screenshot 2025-09-05 at 2.23.11 PM.png' ~/Documents/MazeGame
ubuntu@ubuntu:~/hostshare$ cd ~/Documents/MazeGame
```

```bash
ubuntu@ubuntu:~/Documents/MazeGame$ ls
'Screenshot 2025-09-05 at 2.23.11 PM.png'   clue2.txt
clue1.txt                                   clue3.txt
```

```bash
ubuntu@ubuntu:~/Documents/MazeGame$ ls -a
.   'Screenshot 2025-09-05 at 2.23.11 PM.png'   clue2.txt
..  clue1.txt                                   clue3.txt
```

```bash
ubuntu@ubuntu:~/Documents/MazeGame$ ls -a
.   .secret.txt                                 clue1.txt   clue3.txt
..  'Screenshot 2025-09-05 at 2.23.11 PM.png'   clue2.txt    
ubuntu@ubuntu:~/Documents/MazeGame$ cat .secret.txt
This is secret :O
```

## Testing and Evaluation

### Map The Maze (Part 3)

To evaluate students' knowledge of the command line interface, they used Linux commands to navigate and modify a pre-made 'House' directory. 

The GitHub repository in which this directory can be found is linked [here](https://github.com/thewangclass/CK-Building-Content-Knowledge-Workshop).

To start, the commands below perform the following:

1. Navigate into the house directory using 'cd'
2. Check possible places to navigate to using 'ls'

```bash
ubuntu@ubuntu:~/Documents/CK-Building-Content-Knowledge-Workshop/Unit 1 Activity
- House Exploration$ ls
README.md house
ubuntu@ubuntu:~/Documents/CK-Building-Content-Knowledge-Workshop/Unit 1 Activity
- House Exploration$ cd house
ubuntu@ubuntu:~/Documents/CK-Building-Content-Knowledge-Workshop/Unit 1 Activity
- House Exploration/house$ ls
bedroom1    bedroom2    garage    kitchen   main_entrance
ubuntu@ubuntu:~/Documents/CK-Building-Content-Knowledge-Workshop/Unit 1 Activity
```

The next segment completes the following:

1. Navigate into the main entrance (using 'cd')
2. Find and open a set of instructions in the main entrance (using 'ls' and 'open')
3. Return to the house level (using 'cd')

```bash
ubuntu@ubuntu:~/Documents/CK-Building-Content-Knowledge-Workshop/Unit 1 Activity
- House Exploration/house$ cd main_entrance
ubuntu@ubuntu:~/Documents/CK-Building-Content-Knowledge-Workshop/Unit 1 Activity
- House Exploration/house/main_entrance$ ls
instructions.txt    unopened_mail1.txt    unopened_mail3.txt
shoerack            unopened_mail2.txt
ubuntu@ubuntu:~/Documents/CK-Building-Content-Knowledge-Workshop/Unit 1 Activity
- House Exploration/house/main_entrance$ open instructions.txt
ubuntu@ubuntu:~/Documents/CK-Building-Content-Knowledge-Workshop/Unit 1 Activity
- House Exploration/house/main_entrance$ cd ..
```

This segment checks the kitchen, "eats food" (deletes files), and checks for hidden files.

```bash
ubuntu@ubuntu:~/Documents/CK-Building-Content-Knowledge-Workshop/Unit 1 Activity
- House Exploration/house$ cd kitchen
ubuntu@ubuntu:~/Documents/CK-Building-Content-Knowledge-Workshop/Unit 1 Activity
- House Exploration/house/kitchen$ ls -a
.   ..    .rotten_bananas   banana    cereal    crackers    donut   milk    orange
ubuntu@ubuntu:~/Documents/CK-Building-Content-Knowledge-Workshop/Unit 1 Activity
- House Exploration/house/kitchen$ rm cereal .rotten_bananas
ubuntu@ubuntu:~/Documents/CK-Building-Content-Knowledge-Workshop/Unit 1 Activity
- House Exploration/house/kitchen$ ls -a
.   ..    banana    crackers    donut   milk    orange
```

## Reflection and Analysis

