<h1 align="center">
Bandit Level 26 → Level 27
</h1>

<p align="center">
  <a href="#Level-Goal">Level Goal</a>   |   
  <a href="#Commands-you-may-need-to-solve-this-level">Commands you may need to solve this level</a>   |  
  <a href="#Lets-try">Let's try</a>   |
  <a href="#Solution">Solution</a> 
</p>

## Level Goal
Good job getting a shell! Now hurry and grab the password for bandit27!

## Commands you may need to solve this level:

| command | Explanation |
| ------|-----|
| ls | interactive text editor that is display-oriented: the screen of your terminal acts as a window into the file you are editing. |



## Let's try

- First we will use the same steps using in the previous level to acces to our bandit26 user account. then enter "v" to start Vim editor, then edit the file to set it to /bin/bash with the command

````
:set shell=/bin/bash
````

- then use subshell to list the directory contents using this command 
````
:ls!
````

- finnaly enter "!./bandit27-do cat /etc/bandit_pass/bandit27" for displaying the password 
````
3ba3118a22e93127a4ed485be72ef5ea
````

## Solution 
````
3ba3118a22e93127a4ed485be72ef5ea
````

