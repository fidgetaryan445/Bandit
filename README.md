# Bandit
### Bandit Level 0 
Log into the game using `ssh` command.   

`ssh -p 2220 bandit0@bandit.labs.overthewire.org`  

Password : bandit0

------------------------------

### Bandit Level 1
The password is in *readme* file in home directory

using `more readme`, veiw the contents of the file :  

Password : NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL

------------------------------

### Bandit Level 2 
The password is stored in file with name as *-*.   

To view contents of file use `cat <-` or `more -`.  

Password : rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi

---------------------------------------

### Bandit Level 3 
The password is stored in file with spaces in its name.`more` or `cat` command by default doesnt perceive a filename with spaces. 

To view file contents we will have to use :

..* `more "spaces in this filename"` or `cat "spaces in this filename"` : Here the entire name in *""* will be read as a single file name.  

..* `more spaces\ in\ this\ filename` or `cat spaces\ in\ this\ filename` : Here the backslashes `\` cancels the more to read spaces .  

Password : aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG  

--------------------------------------------

### Bandit Level 4
The password is stored in hidden file in inhere directory .

So first use `cd inhere ` to change directories.  

Then use `ls -a` to show all (including hidden ones) files and directories.  

Use `more .hidden` to access the contents of hidden file .  

. before the name hides the file/ directory .

Password : 2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe

------------------------------------------------

### Bandit Level 5


 
