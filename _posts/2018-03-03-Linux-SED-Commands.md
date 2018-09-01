---
layout: post
title: Linux SED commands
date: 2018-03-03 00:00:00 +0300
description: Linux SED commands # Add post description (optional)
<!-- img: how-to-start.jpg # Add image post (optional) -->
tags: [Programming, Learn, Linux, SED, Shell, terminal] # add tag
comments: true
---

SED commands are used to edit data.

SED means stream editor.

SED commands are used to display and edit data.

Editing options are insert, update, delete.

Two types Operation includes
	1. Lines addressing
	2. Context addressing

Display line multiple times

>> This will show the second line twice

```
sed '2p' file_tab.txt
```

Display ONLY specific line

This will show third line only << -n means only >> cool !!

```
sed -n '3p' file_tab.txt
```
>>> here 3 means line number and p means print thus it prints line 3.

Line addressing

Display line in specific range by:

```
sed -n '2,4p' file_tab.txt
```

If this one in the following done instead then it will not work because the –n is not used:
```
sed '2,4p' file_tab.txt
```

>> It will show that range twice

Likewise; this will show the entire file and the last line twice:
```
sed '$p' file_tab.txt
```

Thus do this to print the last line only:

```
sed -n '$p' file_tab.txt
```

Likewise do not display specific lines by:

```
sed -n '$!p' file_tab.txt
```

Likewise do not display specific range of lines by:

```
sed -n '1,2!p' file_tab.txt
```

Context addressing
>> show specific result by searching key word much like ctr+f
```
sed -n '/ah/p' file_tab.txt
```

>> If you are interested about the case sensitivity then try this:

```
sed -n '/[Aa]h/p' file_tab.txt
```

Write result to a new file just like this simple::

```
sed -n '/[Aa]h/w res.txt' file_tab.txt
```

	VIM / VI commands

New SED command to replace information with new information
This will replace all the 3000 with 6000; simple wowow.
>> s for substitute

sed 's/3000/6000/' file_tab.txt

>> replace multiple data with one command
>> -e means extended operation

```
sed -e 's/3000/6000/' -e 's/4000/6500/' file_tab.txt
```

>> replace data by matching some conditions:

>> Only replace data if certain conditions are met
>> Only for name ah the value will be changed: kust like the following: amazing!!

```
sed '/ah/s/3000/6700/' file_tab.txt
```

>> Delete content of the file just like this:

```
sed '/ah/d' file_tab.txt
```

>> Delete content of the file just like this for capital letter:

```
sed '/[Aa]h/d' file_tab.txt
```

>> Insert or add a line to the file like this:
```
sed '1i/Welcome to data file/' file_tab.txt
```
>> gives an error

command i expects \ followed by text
