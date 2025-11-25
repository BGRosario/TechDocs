# Archiving Files

The archiving file will focus on the command **tar**

tar is the Tape Archiver and was created a long time ago

* By default, it doesn't compress data&#x20;
* Basic use is to compress, extract, or lit&#x20;

```
tar -cvf my_archive.tar /home/etc
tar -tvf will show the contents of an archive
tar -xvf my_archive extracts to the current directory 
    - use -C to switch the output path 
```

* To add compression, use **-z, -j, or J**

Extensions in Linux don't really have meaning, but it helps to see what is going on
