---
layout: post
title: Linux Scripting
date: 2018-03-03 00:00:00 +0300
description: Linux Scripting commands # Add post description (optional)
<!-- img: how-to-start.jpg # Add image post (optional) -->
tags: [Programming, Learn, Linux, Scripting, CAT, Shell, terminal] # add tag
comments: true
---

>> To save log of the commands in script for multiple script press:
>> This will save all the commands in script.log file
script scriptlog.log

>> Script command

-c >>
> it will write all the commands in one file that is pointed

-q >> script -q scriptlog.log
>> this will enter in quite mode
>> if no name is put then system will create a file named typescript

## All uses of CAT commands

1.	View content of file
cat filewithcontent

2.	2. Create new file with content
>> This will create a new file with name filewithcontent
cat > filewithcontent
>> then if you want to add something in the file just type your shit and that’s it
¬	easy huh. Then after adding stuff just press control + c to exit

3.	Copy Content of 1 file to another file
>> this will copy file content to new file
cat filewithcontent > filewithnewcontent

4.	Copy conent of more than 1 file to another file
>> This will copy the content of both file into anotherfile called Resultfile
cat filewithcontent filewithnewcontent > Resultfile
5.	Merge 2 or more files  
¬	This will override the file
¬	This will delete the Resultfile and replace it with Data of Data11
cat Data11 > Resultfile

6.	Append data options
¬	This will append the data instead of replacing it
cat Data11 >> Resultfile


## chmod

1.	Change directory
cd

2.	Copy any files like this following:
cp filename /directory/directory

3.	Move any files just like this
mv filename /directory/directory

4.	Remove a file or folder like this
>> to remove file do this
rm filename
>> to remove a folder do this
rm -r filename

5.	Create backup of file
cat filename > filename_backup

## editors

Many file editors we have vim , emacs, jed

## network commands

1.	to see the location of app do this:
whereis java
2.	To see which application will be run by default compression
which java
3.	How to ping host and output results
ping google.com
4.	Domain information
whois google.com
5.	DNS information
dig google.com
6.	Download file
wget google.com
7.	Download file from where stopped
wget -c google.com

## shell commands - execution

LINUX TUTORIAL – shell commands
114 Shell Scripting basics
>> Kernel
¬	Kernel behave as an interface between user programs or shell and hardware
¬	It is responsible for resource management, resource allocation, reallocation, process management etc
¬	Kernel receive instruction either from user program or shell (user commands)
>> Shell
¬	Shell allow user to interact and access system, it provide shell promt where we can write commands and execute using shell
¬	Shell does not have any GUI, it provide Command line Interface (CLI) for shell programming
¬	It behave as interpreter and interface between user and kernel
¬	We have different type of shell which perform almost same task difference is that they iunderstand different command syntax and different build in function set.
¬	Available shell, BASH, C Shell, Korn Shell, TC Shell, to view my current shell type do this:
echo $SHELL
>> or this
printenv SHELL
>> Shell Script
¬	Shell commands are interactive in nature, we write 1 command and execute it, if we want to perform multiple task in order, we can place all commands in simple txt file and execute it once using shell
¬	This is called shell script. It is same like bat file but more powerful

>> To make shell script just use vim editor then press i to enter insert mode;
>> After creating shell script can do this to execute the file:
./test1.sh
>> or
sh test1.sh

>> Before executing the shell script, you have to change the permission of the shell script file by doing this:
>> This is because shell script has to have rwx : read and write and execute permission which can be given by attaching value 777 to give rwx or 111 to give just x
chmod 777 test1.sh
chmod 111 test1.sh


>> Basics of Shell Script:
# this is for comment line

echo "Hello World"

# variables in shell scripting

# variables are used to hold some data, value of the variable can be changed

# 2 types of variables

# 1 system Defined, already created, written in capital letters

# 2 User defined variables: we can create, small letters, start with alphanumeric and_

# system variable can be seen by typing env

env

>> All system defined variable can be seen b y using env command
>. To display a value of variable echo $varname
>> We can assign value to a variable, just like a=10(no place before after equal)
>> Variables name are case sensitive
>> ‘ ‘ is used for string, but we can not replace any variable
>> “ “ is used for string, and we can replace variable
>> For example
i=10

echo "Your score is $i"
echo 'Your score is $i'

>> Take input from user

echo "Enter your name...."
read i
echo "Your name is $i"

>> but when it will ask for name it will be asked in different line
>> to change this just –n after the echo: just like this

echo –n "Enter your name...."
read i
echo "Your name is $i"


>> Command line parameters : Command line arguments

1.	Whatever we place next to filename is like command line argument
2.	These command line arguments are saved in predefined variables start from $1, $2,… $9( these are called positional parameters
3.	Can be access by $* as well
4.	Total number of command line arguments can be find by $#

>> Command line parameters can be called by doing this:

>> First make a sh file with this

echo $1
echo $2
>> then do this
sh para.sh  hello world
>> for $1  hello and for $2  world
¬	out put will be
	hello
	world

>> Similarly we can do this, make a sh file with this data:
```
echo "Your first name is $1"
echo "Your last name is $2"
echo "Total number of arguments are ---$#"
echo "All arguments are $*"
```

¬	then do this:
sh para.sh  Rakib Fiha

¬	Result will be
¬	Your first name is Rakib
¬	Your last name is Fiha
¬	Total number of arguments are ---2
¬	All arguments are Rakib Fiha

>> Condition Handling
1.	If  - else
2.	If – elif –else
>> Elif can be used any number of times

1.	If –else
>> Create a new sh file with conditioncheck1 with this value:
>> IMPORTANT

# Comparing 2 values

echo -n "Please enter your name-- "
read name

#i="Testing"
if [ $name = "Rakib" ]
then
  echo "correct name entered"
else
  echo "incorrect name entered"
fi

>> IMPORTANT
>> Space has to be maintained for example this following example wont work:
>> Entity has to be separated by space

echo -n "Please enter your name"
read name

#i="Testing"
if [$name="Rakib"] #XXX#
then
  echo "correct name entered"
else
  echo "incorrect name entered"
fi

>> ./conditioncheck1.sh
>> and check the output >>

>> String Comparison
String Comparison		>	Description
str1 = str2 			>	Returns true if the strings are equal
str1 != str2			>	Returns true if the strings are not equal

Rules
Keep space between all entities

>> Numeric Comparison
Numeric Comparison	>	Description
expr1 –eq expr2		> 	Returns true if the expressions are equal
expr1 –ne expr2		>	Returns true if the expressions are not equal
expr1 –gt expr2		> 	Returns true if expr1 is greater than expr2
expr1 –ge expr2		> 	Returns true if expr1 is greater or equal to expr2
expr1 –lt expr2		> 	Returns true if expr1 is less than expr2
expr1 –le expr2		> 	Returns true if expr1 is less or equal to expr2
! expr1			> 	Negates the result of the expressions

# Comparing 2 values

echo -n "Please enter your age-- "
read age

#i="Testing"
if [ $age -ge 23 ]
then
  echo "correct age entered"
else
  echo "incorrect age entered"
fi
2.	If –elif- else

>> Check the following amazing example of elif:
>> In elif you can add multiple elif as many as you want:

# Comparing two values

echo -n "Please enter your deignation - "
read des

if [ $des = 'Manager' ]
then
echo "Designation is manager"

elif [ $des = 'Lead' ]
  then
  echo "Designation is Lead"

else
  echo "Other Designation, and your designation is $des"
fi

Conditional OR and AND
|| and &&


echo -n "Please enter your designation.."
#echo -n " Please enter your deignation ..."
read des

if [ $des = 'Manager' ] || [ $des = 'Director' ]
  then
  echo "you are in grade A"

elif [ $des = 'Lead' ]
  then
  echo "You are in grade B"

else
  echo "You are in grade C"
fi


Loop

for i in 1 2 3 4 5
do
	echo $i
done

>> shortcut to do 1 to 100 loop using seq

for i in $(seq 1 100)
do
        echo $i
done

Functions

Group of code to perform specific task

1.	No Argument No Returned value
2.	Argument but no Returned value
3.	Argument and Returned value

hello ()
{
	echo "This is very simple functiion and bla bla"
}

sum ()

{
	echo "your first name is $1 "
	echo "your second name is $2 "
}

valRet ()

{
	echo "your argument value is $1"
	return 10
}

valRet "Testing"
val=$?
echo $val
>> val=$?
>> This command will take the last output from the function
>> Make sure to put no space there otherwise it will not work
