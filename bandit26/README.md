<h1 align="center">
Bandit Level 25 → Level 26
</h1>

<p align="center">
  <a href="#Level-Goal">Level Goal</a>   |   
  <a href="#Commands-you-may-need-to-solve-this-level">Commands you may need to solve this level</a>   |  
  <a href="#Lets-have-fun">Let's have fun</a>   |  
  <a href="#Lets-try">Let's try</a>   |
  <a href="#Solution">Solution</a> 
</p>

## Level Goal
Logging in to bandit26 from bandit25 should be fairly easy… The shell for user bandit26 is not /bin/bash, but something else. Find out what it is, how it works and how to break out of it.

## Commands you may need to solve this level:

| command | Explanation |
| ------|-----|
| ssh | provides a secure encrypted connection between two hosts over an insecure network |
| cat | allows us to create single or multiple files, view content of a file, concatenate files and redirect output in terminal or files.  |
| more | viewing the contents of a file or files once screen at a time. It supports navigating forwards and backwards through a file and is primarily used for viewing the contents of a file. |
| vi | interactive text editor that is display-oriented: the screen of your terminal acts as a window into the file you are editing. |
| ls | interactive text editor that is display-oriented: the screen of your terminal acts as a window into the file you are editing. |
| id | interactive text editor that is display-oriented: the screen of your terminal acts as a window into the file you are editing. |
| pwd | prints the complete path of the current working directory. |


## Let's try

We have already learned that the shell has many other types  ..
Let's discover the new Shell together ..
-First, let's login to Landit26 from Landit25 like we used to do in previews levels
````
bandit25@bandit:~$ ssh -i bandit26.sshkey bandit26@localhost
````

````
 Enjoy your stay!

  _                     _ _ _   ___   __  
 | |                   | (_) | |__ \ / /  
 | |__   __ _ _ __   __| |_| |_   ) / /_  
 | '_ \ / _` | '_ \ / _` | | __| / / '_ \ 
 | |_) | (_| | | | | (_| | | |_ / /| (_) |
 |_.__/ \__,_|_| |_|\__,_|_|\__|____\___/ 
Connection to localhost closed.

````
The cause of this disconnection is mostly attributed to the new shell.. We know that the /etc/passwd file contains information about the users on the system. Each line describes a distinct user) . then let's look for the information provided by the user bandit 26

````
bandit25@bandit:~$ cat /etc/passwd | grep bandit26.
bandit26:x:11026:11026:bandit level 26:/home/bandit26:/usr/bin/showtext
````

Ok .. so our new Shell is ShowText .. Don't forget that / usr / bin / showtext is a file let's know what we have inside

````
bandit25@bandit:~$ cat /usr/bin/showtext
#!/bin/sh

export TERM=linux

more ~/text.txt
exit 0

````
- export TERM=linux command sets the terminal emulator to linux
-  it uses more command to view ~/text.txt file
-  exit 0 terminat the connection 
ok now we can understand why we can't continue in this session . Therefore, the only way to obtain bandit26‘s password is to gain access to ~/text.txt file BEFORE the connection terminates.

- we know that the more command will not exit if there are more contents to be display. so we have to minimise our terminal prompt’s screen size to ≤ 6 lines, before logging to bandit26..




now with the more command being activated, we can open a Vim text editor (enter v) and view bandit26‘s password file using this command

````
:e /etc/bandit_pass/bandit26
````
:e means  edit the file 
````
5czgV9L3Xx8JPOyRbXh6lQbmIOWvPT6Z
````
## Solution 
````
5czgV9L3Xx8JPOyRbXh6lQbmIOWvPT6Z
````

