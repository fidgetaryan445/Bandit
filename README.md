# Bandit
### Bandit Level 0 
Log into the game using `ssh` command.   

`ssh -p 2220 bandit0@bandit.labs.overthewire.org`  

Password : bandit0

------------------------------

### Bandit Level 1
The password is in *readme* file in home directory

using `more readme`, view the contents of the file :  

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

* `more "spaces in this filename"` or `cat "spaces in this filename"` : Here the entire name in *""* will be read as a single file name.  

* `more spaces\ in\ this\ filename` or `cat spaces\ in\ this\ filename` : Here the backslashes `\` cancels the more to read spaces .  

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

* `-size 1033c` can be used to display only files of size 1033 bytes.

* `! -executable` is used to find non executable file .

* `file` is a bash command to execute it as well we use `-exec file '{}' \;`. Now to only display files of ASCII data type we use `| grep ASCII `

*#NOTE:* `\; ` is used to properly terminate the exec command .  

Password : P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU

-------------------------------------------------

### Bandit Level 7 
The password for the next level is stored somewhere on the server and has all of the following properties:

    owned by user bandit7
    owned by group bandit6
    33 bytes in size

To search the entire directory we will specify *root directory* as starting point using ("/").

In Linux, when you execute a command, there are two primary output streams: standard output (stdout) and standard error (stderr).By default, both stdout and stderr are displayed on the terminal. They are separate streams, but they are often displayed together.

To hide the error output stream we can redirect the error stream(descripitor 2) we can use :

`find / -size 33c  -user bandit7 -group bandit6 2>/dev/null`  #/dev/null: acts as a black hole for data in Linux , hence redirecting stderr to /dev/null esentially discards the data.  

*#Note:* Using 2>/dev/null discard all error messages. If we only want to discard error messages with a particular string we can use 2>&1 to redirect stderr to stdout then we can use grep command to filer out result from stdout.

eg: `find / -size 33c  -user bandit7 -group bandit6 2>&1 | grep -v "Permission denied"`

Password : z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S

----------------------------------------------------

### Bandit Level 8
The password for the next level is stored in the file data.txt next to the word millionth.

To read this line we will use grep command. `grep millionth *` will output all the line in the directory which have millionth word.

For finding the line a specific file such as **data.txt** use : `grep millionth data.txt` .

Password : TESKZC0XvTetK0S9xNwm25STk5iWrBvP

----------------------------------------------------

### Bandit Level 9 
The password for the next level is stored in the file data.txt and is the only line of text that occurs only once.

Use `sort` function to sort the data . Then on sorted output use `uniq -c` to count the number of all different kind of lines appearing.

Now this `uniq -c` outputs the data in 2 column format so using using `-sort k 1n` we will sort the data on the basis of their occurance in the file. 

Finally usinh `head -1` we get the line which only repeats once in the output.

Command is `sort data.txt | uniq -c | sort -k 1n | head -1`

####                                          or 

Use `sort` to sort the data and then use `uniq -u` to print the lines which occur only once.

Command is `sort data.txt | uniq -u`



Password : EN632PlfYiZbn3PhVK3XOGSlNInNE00t  

*NOTE:  `uniq` command only detects adjacent duplicates hence it is important to use `sort` function before using `uniq`*

-------------------------------------------
## Bandit Level 10 
To read human-readble strings in file we can use `strings` command  in linux .

The code will be as follows : `strings data.txt | grep ===` to filter human-readble lines that contain ("===") within them.  

Password : G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s  

------------------------------------------
## Bandit Level 11 
The password is encoded in base64 inside data.txt.

So we will use `base64 data.txt -d`

Password : 6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM

--------------------------------------------
## Bandit Level 12
The password is in data.txt file encoded in rot13 format .

To decode the file we will use translate `tr` command to rotate all the letters .

The translate command will be written as follows `tr [A-Za-z] [N-ZA-Mn-za-m]` .

We have to translate the date of *data.txt* so wewill use :

`more data.txt | tr [A-Za-z] [N-ZA-Mn-za-m]`

It will the translate the data of the output of `more` command i.e. the data of data.txt .

The output is as follows:

`The password is JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv`

Password : JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv

------------------------------------------------
## Bandit Level 13 
The file is a hexdump so first use `xxd -r data.txt ans` . This will convert hexdump back to a text file on which we have to operate.
Now using `xxd *filename* | head ` look at the first bytes of the file . Now from https://en.wikipedia.org/wiki/List_of_file_signatures check for the decompression we need to use. Rename the file accordingly and then decompress the file .

Password : wbWdlBxEir4CaE8LaPhauuOo6pwRmrDw 

------------------------------------------------
## Bandit Level 14 
Use the scp command to copy the private key file from remote system to local system.
Change the permissions of this key file to be executed from `ssh -i` command and then use  `ssh -i` command to login without password.
* `scp -P 2220 bandit13@bandit.labs.overthewire.org:sshkey.private ./try`
* `cd try`
* `chmod 700 sshkey.private`
* `ssh -i /home/manglik242_manas/try/sshkey.private bandit14@bandit.labs.overthewire.org -p 2220`




 
