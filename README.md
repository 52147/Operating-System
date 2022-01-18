# Operating-System

Window's operating system
using GUI (Graphical user interface)
command line intertpteter (CLI).

Linux
using command line interpreter

The command line interpreter in Linux is called a shell,
and the language that we'll use to interact with this shell is called Bash.

Basic Operating System Navigation
1. Navigating from one directory to another
2. Getting file information
3. Removing files and directories

File and Text Manipulation

1. Searching through your directories
2. Find a specific file
3. Copying and pasting
4. Changing commands

Path

C:\Users\Cindy\Desktop
In Windows, filesystems are assigned to drive letters, which look like C:, or D:, or X:.

root directory
each file system has a root directoty 
which is the parent for all other directories in that file system.

The root directory of C: would be written C:\,
and the root directory of X: would be written X:\


Subdirectories are separated by backslashes(\), unlike Linux, which used forward slashes (/).

main directory
The main directory in a Wnidow system is the drive that the file system is stored on.
In this case, our file system is stored on Local Disk C.
go to Users, then my User folder cindy, and finally to Desktop.
If you look at the top here, you can see the path.

-> C:\Users\Cindy\Desktop

In the desktop directory that we have a few folders and files.
There are some files on here we can't see.
We call these hidden files.
They are hidden for few reasons.
 1. One is that we do not want anyone to see or accidentally modify these files.
 They could be critical system files or configs.
  ex: secret_file
  
file information
file name
type of file
application to oppen
location path C:\User\cidy\Desktop
The size of the file
The size on disk
when the file was created
last modified,
and last accessed.

file attributes we can enable for our file:

read-only
hidden

Security tab
Details tab
Previous Versions tab: lets us restore an earlier version of a file
so if you made a change to a file and wanted to revert to that change, you can go back to that version.


List directories in CLI(command line interface)

A couple of command line interfaces(CLI) available in Windows.
1. The first is called the Command Prompt, command.exe.
2. The second is PowerShell or powershell.exe.

Command prompt
It's similar to the command prompt that was used in MS DOS,
since powershell supports most of the same commands as Command Prompt, and more.
We are going to use PowerShell for the exercises.
Many PowerShell commands that we use are actually aliases for common commands in other shells.
alias is a nickname for a command.

## ls C:\

The first command that we'll use is for listing files and directories.
Let's start by listing the directories in the root of our C: drive.
The C: drive is where  Windows operating system is installed.
It might be only hard drive that you have in your computer.

1.  To get the PowerShell CLI, just search in your application's p list PowerShell.
2.  
We are going to use the ls (list directory command) and give it the path of where we want to look.
The path is not part of the command, but it is a command parameter.
parameter is a value that is associtaed with a command
3.
Now you can see all the directories in the root of your C: drive.

The C: drive root folder is what we we call a parent directory
and the content inside are considered child directories.

common child directoties in this folder:

Program Files x86:

These directories contain most of the applications and other programs that are installed in Window.

Users:
This contains the user profile directories or home directories.
Each user who logs into this Wnidow machine will get their own directory here.

Windows:
Windows, this is where the Windows operatong system is installed.


## Get-Help ls
we'll see the text describing the parameters of the ls command.
This will give us a brief summary of the commands parameter.

## Get-Help ls-Full
we can see more detailed help
you can see a descriptuin of each of the parameters and some examples of how to use the command.

## -Force
we can see all teh hidden files in the directory
The -Force paremeter will show hidden and system files that aren't normally listed with just ls.
Now you can see more important files and directories such as Recycle Bin.

Recycle Bin:
When you move files to the Recycle Bin, they move to this directory
instead of being deleted immediately.

Progtam data:
This directory contains lots of different things.
In general, it's used to hold data for programs that are installed in Program Files.










  

  
