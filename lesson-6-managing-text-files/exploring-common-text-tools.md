# Exploring Common Text Tools

On Linux you will find many tools to read the text of a content&#x20;

* **more** was the original file pager&#x20;
* **less** was developed to offer some more advanced features&#x20;
* As a reaction to that, **more** was developed a bit more&#x20;
* But still, to do more, use **less**
* In particular, in **less** you can easily scroll forwards as well as backwards in files

***

## Cut command

Cut is a command-line utility that allows you to cut parts of lines from specified files or piped data and print the result to standard output. It can be used to cut parts of a line by delimiter, byte position, and character&#x20;

* cut _filename_ = Does not work&#x20;
* cut --_version_ = Check Version
* cut -c1 _filename_ = list one character
* cut -c1, 2, 4 = pick and chose character
* cut -c1 -3 _filename_ = List range of characters
* cut -c1 -3, 6-8 _filename_ = List specific range of characters&#x20;
* cut -b1 -3 _filename_ = List by byte size
* cut -d: -f 6 /etc/passwd = List first 6th column separated by:&#x20;
* cut -d: -f 6-7 /etc/passwd = List first 6 and 7th column separated by:
* ls -l | cut -c2 -4 = Only print user permissions of files/dir&#x20;
