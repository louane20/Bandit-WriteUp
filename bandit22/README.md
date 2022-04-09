<h1 align="center">
Bandit Level 21 → Level 22
</h1>

<p align="center">
  <a href="#Level-Goal">Level Goal</a>   |   
  <a href="#Commands-you-may-need-to-solve-this-level">Commands you may need to solve this level</a>   |  
  <a href="#Lets-have-fun">Let's have fun</a>   |  
  <a href="#Lets-try">Let's try</a>   |
  <a href="#Solution">Solution</a> 
</p>

## Level Goal
A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

- NOTE:<br/> Looking at shell scripts written by other people is a very useful skill. The script for this level is intentionally made easy to read. If you are having problems understanding what it does, try executing it to see the debug information it prints.

## Commands you may need to solve this level:
| command | Explanation |
| ------|-----|
| cron | Explanation |
| crontab | opens the cron table for editing  |


## Let's have fun

Well.. in the previous level we used the shell script, but our use of it was superficial so we did not go into depth with it.. but the note added to this level indicates that we need to understand it well..

- What is shell script?<br/>
A shell script is a text file that contains a sequence of commands for a UNIX-based operating system. It is called a shell script because it combines a sequence of commands, that would otherwise have to be typed into the keyboard one at a time, into a single script. The shell is the operating system's command-line interface (CLI) and interpreter for the set of commands that are used to communicate with the system.

- How shell scripting works?
The basic steps involved with shell scripting are writing the script, making the script accessible to the shell and giving the shell execute permission.

Shell scripts contain ASCII text and are written using a text editor, word processor or graphical user interface (GUI). The content of the script is a series of commands in a language that can be interpreted by the shell. Functions that shell scripts support include loops, variables, if/then/else statements, arrays and shortcuts. Once complete, the file is saved typically with a .txt or .sh extension and in a location that the shell can access.

- (#!/bin/bash ) What exactly is this ?
This first line (#!/bin/bash or #!/bin/sh) has a name. It is known as ‘she-bang‘(shabang). This derives from the concatenation of the tokens sharp (#) and bang (!).  it tells the shell what program to interpret the script with, when executed.
We have often seen variety of she-bang or script header. We often wonder why is that particular script using that particular she-bang, why not some other. On Unix-like Operating systems we have a choice of multiple shells. The shell is responsible not only for the little prompts but also interpreting the commands of the script. Thus the shell plays an important role specially when we implement big and complex logics using conditions, pipes, loops , etc. /bin/bash is the most common shell used as default shell for user login of the linux system. The shell’s name is an acronym for Bourne-again shell. Bash can execute the vast majority of scripts and thus is widely used because it has more features, is well developed and better syntax.

## Let's try
Well..it seems that this level is similar to the previous one..so let's try first to follow the same steps with complete stupidity, then let's go deeper and explain everything in detail.

- First, let's go to the directory /etc/cron.d/ and take a look at what's inside. Since we are looking for the bandit 23 password, let's read the file cronjob_bandit23. In it we will find the script cronjob_bandit23.sh. Let's see what it contains.
````
bandit22@bandit:~$ cd  /etc/cron.d/

bandit22@bandit:/etc/cron.d$ ls
cronjob_bandit15_root  cronjob_bandit17_root  cronjob_bandit22  cronjob_bandit23  cronjob_bandit24  cronjob_bandit25_root

bandit22@bandit:/etc/cron.d$ cat cronjob_bandit23
@reboot bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null
* * * * * bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null

bandit22@bandit:/etc/cron.d$ cat /usr/bin/cronjob_bandit23.sh
#!/bin/bash
myname=$(whoami)
mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)
echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"
cat /etc/bandit_pass/$myname > /tmp/$mytarget

````

- hmm, it seems strange we didn't understand anything.. well let's follow the advice and try to execute it
````
bandit22@bandit:/etc/cron.d$ . /usr/bin/cronjob_bandit23.sh
Copying passwordfile /etc/bandit_pass/bandit22 to /tmp/8169b67bd894ddbb4412f91573b38db3
````

- Oh amazing it seems that it copy the password from the file that we do not have permission "/etc/bandit_pass/bandit22" to  "/tmp/8169b67bd894ddbb4412f91573b38db3". Let's see what we have inside this file

````
bandit22@bandit:/etc/cron.d$ cat /tmp/8169b67bd894ddbb4412f91573b38db3
Yk7owGAcWjwMVRwrTesJEwB7WVOiILLI
````


We got it successfully!!

- Now let's go back a bit and try to understand what's going on here.
````
#!/bin/bash
myname=$(whoami)
mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)
echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"
cat /etc/bandit_pass/$myname > /tmp/$mytarget
````
In general, we understand from the script that the password is stored in the file named $mytarget
in which
-$mynam = bandit23
-cut  is a command for cutting out the sections from each line of files and writing the result to standard output. It can be used to cut parts of a line by byte position, character and field.
-md5sum  is designed to verify data integrity using MD5 (Message Digest Algorithm 5).
MD5 is 128-bit cryptographic hash and if used properly it can be used to verify file authenticity and integrity.

Amazing.. Now we understand the contents of the script


## Solution 
````
bandit22@bandit:/etc/cron.d$ cat /tmp/8169b67bd894ddbb4412f91573b38db3
Yk7owGAcWjwMVRwrTesJEwB7WVOiILLI
````


