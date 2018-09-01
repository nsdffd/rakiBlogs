---
layout: post
title: Linux GREP commands
date: 2018-03-03 00:00:00 +0300
description: Linux GREP commands # Add post description (optional)
<!-- img: how-to-start.jpg # Add image post (optional) -->
tags: [Programming, Learn, Linux, GREP, Shell, terminal] # add tag
comments: true
---

GREP stands for Global Regular Expression Parsel
It is used to search data in one or more file

Command 1: Search data I 1 file

Command 2: Search data in more than 1 file

Command 3: Search data in all files in current directory

If you want to search something in a file: do this:

>> This will search for the word ah in file named file_tab_txt

```
grep ah file_tab.txt
```

If you want to search something in two or more files: then use the following;
>> This will look for ah in file_tab.txt and file_tab 2.txt
>> tips: use backslash if you want to choose a file that has a space

```
grep ah file_tab.txt file_tab\ 2.txt
```

If you want to search something then use the following;
```
grep "update" process.txt
```

But if you want to search for something in a directory for whole files then

>> If you want to search something in a directory then use the following;

>> If you want to search that ends with specific format then do this:

>> This will look for the word ah in all txt format files in the directory
```
grep ah
```
```
*.txt
```

If you want to search for all formats then do this:
>> This will look for the word update in all files in the directory
```
grep update
```
```
*.*
```

This will look for the word “Ah” in file_tab 2.txt
>> Grep looks for case sensitivity
```
GREP "Ah" file_tab\ 2.txt
```

To ignore case sensitivity use the following command:
```
grep -i ah file_tab\ 2.txt
```

To get line number for specific words in the file do the following
```
grep -n ah file_tab\ 2.txt
```

It also possible to remove case sensitivity by doing this

```
grep -n -i ah file_tab\ 2.txt
```

This will look for the word ah in all txt format files in the directory
but if you just want to see the file instead of seeing the word besides the file type this:
```
grep -l ah
```
```
*.txt
```
```
grep -l ah
```
```
*.*
```
Search data with exact word:
>> -w means exact word
```
grep -w ah file_tab\ 2.txt
```

Search record with except search condition
>> if you want to search something that does not have specific data then do this:
>> -v means reverse

This will show everything that does not have ah in it
```
grep -v ah file_tab\ 2.txt
```
>> To consider case sensitivity, you can do the following:

```
grep -v -i ah file_tab\ 2.txt
grep -v [Aa]h file_tab\ 2.txt
```
>> Display next before surrounding:
>> -A 1 after the line
>> -B 1 before the line
>> -C 1 After and before the line

This will show two line before the search result
```
grep -B 2 dh file_tab\ 2.txt
```
This will show two line after the search
```
grep -A 2 dh file_tab\ 2.txt
```
This will show two line before the search and two line after the search
```
grep -C 2 dh file_tab\ 2.txt
```

Display number of matches:
>> -c will show how many times something is there in the result

This will display number of times 3000 is there in the result
```
grep -c 3000 file_tab\ 2.txt
```

Search multiple data in one command:
>> -n is optional >> it will show the line number
>> -e to add more search items

This one will look for ah and dh in the file_tab2 .txt
```
grep -n -e ah -e dh file_tab\ 2.txt
```

Using Egrep >> Extended grep
>> this will give the same result like before and will show two search result
```
egrep 'ah|dh' file_tab\ 2.txt
```
>> Make sure that double quote or single quote because of the pipe

This will show all the process where there is bin including the lines and without the word bin in the lines respectively

```
grep -n bin process2
grep -n -v bin process2
```

This will show all the process where there is bin including the lines and without the word bin in the lines respectively

>> This will show how many times bin comes up
```
grep -c bin process2
```
>> This will show how many times exact word is shown:
```
grep -c -w bin process2
```
>> This will show the line numbers of exact word bin
```
grep -n -w bin process2
```

>> didn’t work fully
```
grep -n -B 2 -v bin process2
```
