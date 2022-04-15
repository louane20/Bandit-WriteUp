<h1 align="center">
Bandit Level 23 → Level 24
</h1>

<p align="center">
  <a href="#Level-Goal">Level Goal</a>   |   
  <a href="#Commands-you-may-need-to-solve-this-level">Commands you may need to solve this level</a>   |  
  <a href="#Lets-have-fun">Let's try</a>   |
  <a href="#Lets-try">Let's try</a>   |
  <a href="#Solution">Solution</a> 
</p>

## Level Goal
A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

- NOTE:<br/> This level requires you to create your own first shell-script. This is a very big step and you should be proud of yourself when you beat this level!

- NOTE 2:<br/> Keep in mind that your shell script is removed once executed, so you may want to keep a copy around…

## Commands you may need to solve this level:
| command | Explanation |
| ------|-----|
| cron | Explanation |
| crontab | opens the cron table for editing  |


## Lest's hae fun
Look, they said we'll write the script this time.. that's cool.. looks like we're going to have a lot of fun
Well, we have already learned the basics of Shell.. Now let's learn how to write a Shell script

# General principles of shell scripting

A shell script is a series of commands. we have already manipulated the shell on the command line, so we can start our first scripts.

- comments

Almost all computer languages allow the insertion of comments. To do this, simply precede each comment line with the character “#”.
````
#this is a comment
````

 - condition
The shell offers two main ways to perform a test
````
test expression
[expression]
````

- The if condition
````

if condition 
 then commands
elif condition
 then commands
else commands 
fi
````

- The case condition
````
case string in
  pattern) commands ;;
  pattern) commands ;;
esac
````

- The while loop
````
while
  do commands
done
````

- The for loop
````
for var in list of strings
do commands
done
````


## Let's try
 
- First, let's follow the steps of the previous level to see what we have inside the file cronjob_bandit24

````
bandit23@bandit:~$ cd /etc/cron.d
bandit23@bandit:/etc/cron.d$ ls
cronjob_bandit15_root  cronjob_bandit17_root  cronjob_bandit22  cronjob_bandit23  cronjob_bandit24  cronjob_bandit25_root
bandit23@bandit:/etc/cron.d$ cat cronjob_bandit24
@reboot bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
* * * * * bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null

````

- It looks like it will send us as before to the shell script with the same file name.. well, we have learned shellscript in previous levels and understand its basics, so let's try to analyze the script in front of us
````
bandit23@bandit:/etc/cron.d$ cat /usr/bin/cronjob_bandit24.sh
#!/bin/bash

myname=$(whoami)

cd /var/spool/$myname
echo "Executing and deleting all scripts in /var/spool/$myname:"
for i in * .*;
do
    if [ "$i" != "." -a "$i" != ".." ];
    then
        echo "Handling $i"
        owner="$(stat --format "%U" ./$i)"
        if [ "${owner}" = "bandit23" ]; then
            timeout -s 9 60 ./$i
        fi
        rm -f ./$i
    fi
done
````
- myname = bandit24
- 


## Solution 


