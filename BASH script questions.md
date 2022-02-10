### 1. Find the last modified files within 3 hours
Ans find . -mtime -0.12

## 2. Given a Log file, How many 404 error codes are there in the file
Ans 
find /home/pranav -type f -name "2020_04_22.shared_http_server.192.168.XX.XX.log" |while read file
  do
    RESULT=$(egrep "[^0](404)" $file)
      if [[ ! -z $RESULT ]]
         then
            echo "Error(s) in $file on $HOSTNAME at "$(date)": $RESULT">> log_result.txt
     fi
  done
  
## 3. Display the first 3 lines & last line from the file using bash command 
ANs -
 tail -3 filename (last 3 lines) \n 
 head -3 file name (First 3 lines)
 
## 4. /bin/bash VS /bin/sh?
Ans -
#!/bin/sh :Executes the script using the Bourne shell or a compatible shell, with path /bin/sh
#!/bin/bash :Executes the script using the Bash shell.
#!/bin/csh -f :Executes the script using C shell or a compatible shell.
#!/usr/bin/perl -T :Executes the script using perl with the option of taint checks
#!/usr/bin/env python :Executes the script using python by looking up the path to the python interpreter automatically from the environment variables

## 5. What does #! Mean in Linux?
Ans -
#! specifies the program with which the script should be executed if you not explicitly call it which any.

## 6. 8: Use sed command to replace the content of the file (emulate tac command)
Eg:
if cat fille
ABCD
EFGH

Then O/p should be

EFGH
ABCD

ANS - sed '1! G; h;$!d' file1
Here G command appends to the pattern space,
h command copies pattern buffer to hold buffer
and d command deletes the current pattern space.

## 7. Given a file, replace all occurrence of word “ABC” with “DEF” from 5th line till end in only those lines that contains word “MNO”

ANS - sed –n '5,$p' file1|sed '/MNO/s/ABC/DEF/'

## 8. Given a file, write a command sequence to find the count of each word.
ANS -
tr –s  "(backslash)040" <file1|tr –s  "(backslash)011"|tr "(backslash)040 (backslash)011" "(backslash)012" |uniq –c
where "(backslash)040" is octal equivalent of "space"
“(backslash)011” is an octal equivalent of “tab character” and

“(backslash)012” is an octal equivalent of the newline character.

## 9.How will you find the 99th line of a file using only tail and head command?
ANS-
tail +99 file1|head -1

## 10.Print the 10th line without using tail and head command.
ANS-
sed –n '10p' file1

## 11. What is the difference between $$ and $!?
ANS-
$$ gives the process id of the currently executing process whereas $! Shows the process id of the process that recently went into the background.

## 12. I want to connect to a remote server and execute some commands, how can I achieve this?
ANS-
We can use ssh to do this:
ssh username@serverIP -p sshport
Example
ssh root@122.52.251.171 -p 22
Once above command is executed, you will be asked to enter the password.

## 13. I have 2 files and I want to print the records which are common to both.
ANS-
We can use “comm” command as follows:
command - comm -12 file1 file2 
12 will suppress the content which are unique to 1st and 2nd file respectively.

## 14. Write a script to print the first 10 elements of Fibonacci series.
ANS-  
#!/bin/sh
a=1
b=1
echo $a
echo $b
for I in 1 2 3 4 5 6 7 8
do
c=a
b=$a
b=$(($a+$c))
echo $b
done

## 15. What are the 3 standard streams in Linux?
ANS-
0 – Standard Input
1 – Standard Output
2 – Standard Error

## 16. Given a file find the count of lines containing the word “ABC”.
ANS-
grep –c “ABC” file1

## 17. How will you print the login names of all users on a system?
ANS-
/etc/shadow file has all the users listed.
Command - awk –F ':' '{print $1}' /etc/shadow|uniq -u

## 18. How to set an array in Linux?
ANS-
Syntax in ksh://
Set –A arrayname= (element1 element2 ….. element)
In bash//
A=(element1 element2 element3 …. elementn)

## 19. Write down the syntax of “for ” loop
ANS-
Syntax:
for  iterator in (elements)
do
execute commands
done

## 20. How will you find the total disk space used by a specific user?
ANS-
du -s /home/user1 ….where user1 is the user for whom the total disk space needs to be found.

## 21. Write the syntax for “if” conditionals in Linux?
ANS-
Syntax//
If  condition is successful//
then//
execute commands//
else//
execute commands//
fi//

## 22. How do we delete all blank lines in a file?
ANS-
sed  '^ [(backslash)011(backslash)040]*$/d' file1


where (backslash)011 is an octal equivalent of space and
(backslash)040 is an octal equivalent of the tab

## 23.How will I insert a line “ABCDEF” at every 100th line of a file?
ANS-
sed ‘100i\ABCDEF’ file1

## 24. Write a command sequence to find all the files modified in less than 2 days and print the record count of each.
ANS -
find . –mtime -2 –exec wc –l {} \;

## 25.  How can I set the default rwx permission to all users on every file which is created in the current shell?
ANS-
We can use:
umask 777

## 26. How can we find the process name from its process id?
ANS-
We can use “ps –p ProcessId”
