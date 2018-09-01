---
layout: post
title: Linux AWK commands
date: 2018-03-03 00:00:00 +0300
description: Linux AWK commands # Add post description (optional)
<!-- img: how-to-start.jpg # Add image post (optional) -->
tags: [Programming, Learn, Linux, AWK, Shell, terminal] # add tag
comments: true
---

cat file_tab.txt
 1. To list each row of a file

awk '{print $1}' file_tab.txt
awk '{print $2}' file_tab.txt
awk '{print $1$3}' file_tab.txt
awk '{print $1 "  " $3}' file_tab.txt

for entire file to print
awk '{print $0}' file_tab.txt


2. awk to show csv files

awk -F "," '{print $1}' file_tab.txt

or>

awk '{print $1}' FS="," file_tab.txt

2. print file without the header:

¬	This one does not display the first row
awk 'NR!=1{print $1"  " $2}' file_tab.txt
awk 'NR>=2{print $1"  " $2}' file_tab.txt

¬	This one only displays row 2
awk 'NR==2{print $1"  " $2}' file_tab.txt

3. Saving result to a file:

eg.

awk -F "," '{print $1 " " $2}' file_tab.txt > file_result.txt

4. Row Filtering

>> It will show only the value that has 1 in row 1.

awk -F "," '$1==1{print$1"  "$2}' file_tab.txt

>> It will show only the values that have sh in row 2

awk -F "," '$2=="sh"{print$1"  "$2}' file_tab.txt

>> It will show only the values that have 2000 or higher value in row 3

awk -F "," '$3>=2000{print$1"  "$2}' file_tab.txt


>>> Row filtering with or statement

awk -F "," '$3>=2000 || $1==2{print$1"  "$2}' file_tab.txt

>>> Row filtering with logical and statement

awk -F "," '$4=="aj" && $3==3000{print$1" "$2}' file_tab.txt

5. Display specific string from anywhere in the row

>> This will find all the Aj the row

awk -F ","  '/Aj/{print$0}' file_tab.txt

>> from specific column

awk -F "," '$2~/sh/{print$0}' file_tab.txt

>> For specific string to be shown up
awk -F "," '$2=="sh"{print$0}' file_tab.txt

>> And when to find specific string not present in specific column:
awk -F "," '$2!~/sh/{print$0}' file_tab.txt

>> Display content that starts with specific letter
>> Find text at the beginning of the line
>> Only the ^ character can do it, so easy::
>> This will find that starts with s:

awk -F "," '$2~/^s/{print$0}' file_tab.txt

>> Find text at the end of the line
>> Display content that ends with specific letter
>> Find text at the end of the line
>> Only the $ character can do it, so easy::
>> This will find stuff that ends with s:

awk -F "," '$2~/s$/{print$0}' file_tab.txt

for example:

>> This will print row 8 that has /usr at the beginning:

awk '$8~/^\/usr/{print$0}' process.txt


____start from_____ 19

Perform condition checking using if-else statement in awk:

>This will print values greater than 2000 for column 3 in column 2 otherwise will print triple star. ***
```
awk -F "|" '{if($3>=2000) print $2;
else print "***" ;}' file_tab.txt
```

>> Perform condition checking using if-else and then else if statement in awk:
 >>>> MAKE SURE TO COPY THE DOUBLE QUOTE CORRECTLY
awk -F "|" '{
>if($3>=3000) print $2 “Your tax is 30%”;
>else if ($3>=2000) print $2 “Your tax is 20%”;
>else print $2 “Your tax is 10%”;}' file_tab.txt

{Begin Block}{Action Block}{End Block}

>> Begin Block
>> This will double the entire column if column 3 is 3000 >> Java or C++ .
awk -F "|" 'BEGIN{salary=2}{if($3==3000){ $3=$3*2; print$0;}}' file_tab.txt

>> In End block it says the action is done, end block is not mandatory
>> End Block
>> Add functional programming in awk commands
>> For example this one in the following shows how many times are the same values are recorded in a file: just like that.. amazing!!!!

awk -F "|" 'BEGIN{count=0;print "Here is the value"}{if($3==3000){print $0;count=count+1;}}END{print "Task is done " count " times"}' file_tab.txt

While loop in awk in the terminal >>
>> Print some stuff twice

awk -F "|" '{
i=1;
while(i<=2)
{
print $0;
i++;
}
}' file_tab.txt

More example of while loop, for example this one will show each column in different row

awk -F "|" '{
i=1;
while(i<=3)
{
print $i;
i++;
}
}' file_tab.txt

For loop
>> Print some stuff twice like done in while loop before>>
>>> while loop would make it work great looks fooking amazing this linux shit.
>> I am in love with awk

awk -F "|" '
{   
for(i=1;i<=2;i++)
{
print $0
}   
} ' file_tab.txt

>>>> For loop to do other crazy amazing stuff
>> like killing some werid shit
>> if you put NR!=1 within a single quote, the first line sucks litself
>> that means first line does not show up anymore
>> also to make it show up in a row instead of column do for or while loop, it will work like a charm like the following:

awk -F "|" 'NR!=1
{
for(i=1;i<=3;i++)
{
print $i;
}
} ' file_tab.txt

Storing command result into a variable

Suppose we want to save result of this command:

awk -F "|" 'NR!=1 {print $2}' file_tab.txt

then do this

a=`awk -F "|" 'NR!=1 {print $2}' file_tab.txt`

echo $a

you can see all the results are stored in variable a. make sure that closing command is not single quote.
