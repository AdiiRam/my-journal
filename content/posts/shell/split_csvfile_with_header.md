---
title: "Splitting Large CSV File with Header"
date: 2019-04-06
draft: false
toc: true
images:
tags:
 - shell
 - csv

---

Introduction
------------

Splitting large files is a very common operation that I do and mostly its done using number of lines as the split criteria. I use the **split** command that is available in bash . I won't get into the specifics of how to use the split command as there are many tutorials available online. 

In this article , I will share a specific scenario that I had . The scenario is I have a large CSV File along with header and I had to split the file into smaller parts such that each part also retained the header . The native split command is very generic and as such has no inbuilt support for this. 

To achieve this , I had to use the combination of **split** and **sed** commands. 
The code snippet below not only does the splitting , but also ensures that the split files contain header as well. 

```bash
   
   # Step 1 : Get the Header from the large CSV File as indicated by inputfile
   headerrow=`head -n 1 $inputfile`

   # Step 2 : Delete the Header from the input file and store the resulting contents into tmpfile. 
   # Deletion is not done inline , so as to retain the inputfile . 
   sed '1d' $inputfile > $tmpfile

   # Step 3 : Split the tmpfile , providing the split criteria which in this case is the number of lines and also providing the prefix to be used.  
   split -l $nooflines ../$tmpfile $prefix

   # Step 4 : Add the header to each of the split file 
   # partfile is the split file . 
   sed -i "1i$headerrow" $partfile; 
```

The overall bash script is available in github [here](https://github.com/AdiiRam/shell_kb/blob/master/resources/split_csvfiles_with_headers.sh)