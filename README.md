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
The password is stored in only human readable file i.e. the files in the directory will have Binary data type except for one humanly readable whcih will be ASCII.  

To find such file in directory we can change directory to inhere and then use `file ./*`  

Password : lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR

--------------------------------------------

### Bandit Level 6
The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:

    human-readable
    1033 bytes in size
    not executable
    
To use find with such properties we can use :  

..* `-size 1033c` can be used to display only files of size 1033 bytes.

..* `! -executable` is used to find non executable file .

..* `file` is a bash command to execute it as well we use `-exec file '{}' \;`. Now to only display files of ASCII data type we use `| grep ASCII `

*#NOTE:* `\; ` is used to properly terminate the exec command .  

Password : P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU




 
