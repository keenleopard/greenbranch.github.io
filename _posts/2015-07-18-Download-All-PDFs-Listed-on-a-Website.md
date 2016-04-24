---
layout: default
title: Download All Pdfs listed on a website
---

#How to download all pdfs listed on a website

Sometimes I found a course website that contains a bunch of slides, notes, and exercises. It will be tidious to open all links one by one and download them one by one, therefore I found a good approach to **download all pdfs on a website**

The first step is to linke all external lines that ended in **.pdf**. It can be down in this way:

```
lynx -dump http://website.html | grep .pdf > file.txt
```	

the commmand before the pipe is to display all links on the website and the command after is to write those links ending in .pdf to a txt file. 

Yet if you open files.txt you will find the format is something like this:

	23. http://website.html/Lecture1.pdf
	35. http://website.html/Lecture2.pdf

The first colum is the number index for the link. This will cannot be read if you want to use wget to download the files. The numbers can be removed in this way:

	awk '{print $2}' < file.txt > file_md.txt
	
and now the format will look like:
	
	http://website.html/Lecture1.pdf
	http://website.html/Lecture2.pdf
	
Then we can use weget to download all the links by one command:

	wget -i file_md.txt
	
That's it, quite simple :)

