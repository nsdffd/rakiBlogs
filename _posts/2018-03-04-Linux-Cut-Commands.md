---
layout: post
title: Linux File Processing using CUT commands
date: 2018-03-03 00:00:00 +0300
description: Linux CUT commands # Add post description (optional)
<!-- img: how-to-start.jpg # Add image post (optional) -->
tags: [Programming, Learn, Linux, Cut, Shell, terminal] # add tag
comments: true
---

GREP stands for Global Regular Expression Parsel

Tips:
>> this will show the number of lines of the file
wc -l process2
>> this will also show the content including the lines
cat -n file_tab\ 2.txt


content cutting
>> this will cut from character 3 to character 8
cut  -c3-8 file_tab\ 2.txt

>> this will cut from character 3 without range
cut  -c3- file_tab\ 2.txt
>> this will cut to character 10
cut  -c-10 file_tab\ 2.txt

> > content cutting for specific column
>> this will show the column 2
cut -d "|" -f2 file_tab.txt
>> Display specific range of column:
>> This will show from column 2 to column 3
cut -d "|" -f2-3 file_tab.txt
>> This will show from column 2 till the end
cut -d "|" -f2- file_tab.txt

>> All the column except specific column
>> It does not work in macOS, since –complement is not supported in MacOS
cut -d "|" --complement -f2 file_tab.txt
