<h1 align="center">
Bandit Level 21 → Level 22
</h1>

<p align="center">
  <a href="#Goal">Level Goal</a>   |   
  <a href="#Cmd">Commands you may need to solve this level</a>   |  
  <a href="#fun">Let's have fun</a>   |  
  <a href="#Try">Let's try</a>   |
  <a href="#Solution">Solution</a> 
</p>

## Level Goal:
A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

## Commands you may need to solve this level:
| command | Explanation |
| ------|-----|
| cron | Explanation |
| crontab | opens the cron table for editing  |


## Let's have fun:

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

Since we are using the user Pandit 21 no root then we cannot use crontab.
So let's go to the /etc/cron.d/ directory and see what it contains
````
bandit21@bandit:~$ cd /etc/cron.d/
````

## Solution 


