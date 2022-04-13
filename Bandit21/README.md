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

## Commands you may need to solve this level:
| command | Explanation |
| ------|-----|
| cron | Explanation |
| crontab | opens the cron table for editing  |


## Let's have fun

Through the given text, we notice the presence of the word cron, so what is cron and why should we review the file /etc/cron.d/ ?

- What is Cron?<br/>
Cron is a program for automatically executing scripts, commands or software at a precise specified date and time, or according to a cycle defined in advance.</br>

- What is Crontab?<br/>
Each user has a crontab file, allowing him to indicate the actions to be performed.</br>

- crontab, crontab(5) what's the difference?<br/>

crontab(1) is the man page[^1] of crontab command.
[^1]: The man pages are divided in sections. Each section groups similar man pages. For example, Section 1 holds user commands (commands runable by all users in the system). Section 8 covers SysAdmin commands (the commands that demand root access to be run). Section 5 covers file formats.

crontab(5) is the man page of crontab file.

- How does Cron work?<br/>
Scheduled cron jobs are defined at the system level in the /etc/crontab file and in the /etc/cron.d/ folder
To modify your scheduled tasks type: crontab -e. Tasks defined in crontab are executed by root.<br/>
Here is a short description of the structure of an entry in a crontab file:<br/>
minute hour days_in_the_month month day_of_the_week The_command_to_run.

## Let's try

- Since we are using the user Bandit21 not root then we cannot use crontab.
- So let's go to the /etc/cron.d/ directory and see what it contains
````
bandit21@bandit:~$ cd /etc/cron.d/
````
- list available files
````
bandit21@bandit:/etc/cron.d$ ls
cronjob_bandit15_root  cronjob_bandit17_root  cronjob_bandit22  cronjob_bandit23  cronjob_bandit24  cronjob_bandit25_root
````
- we are looking for the password bandit22 so we should use cronjob_bandit22 (if you test the others you will find the same cron job with different scripts cronjob_bandit17-->cronjob_bandit17.sh without reboot option -if you follow the script you won't find anything-)
````
bandit21@bandit:/etc/cron.d$ cat cronjob_bandit22
@reboot bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
* * * * * bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
````
According to what we learned a little while ago. We conclude that every second the shell script cronjob_bandit22.sh is executed. Let's see what we have inside this script

 The @reboot is an special keyword that is used by cron to run a job when the system is rebooted.

````
bandit21@bandit:/etc/cron.d$ cat /usr/bin/cronjob_bandit22.sh
#!/bin/bash
chmod 644 /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
cat /etc/bandit_pass/bandit22 > /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv

````
First this script gives some permission to the file t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv , and then receives the data provided in the file /etc/bandit_pass/bandit22 from the directory name we can expect that we will finally find the password. let's make sure
````
bandit21@bandit:/etc/cron.d$ cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
Yk7owGAcWjwMVRwrTesJEwB7WVOiILLI
````

## Solution 
````
bandit21@bandit:/etc/cron.d$ cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
Yk7owGAcWjwMVRwrTesJEwB7WVOiILLI
````

