# Lesson 3. Essential Tools

This will focus on how to use MAN, text editors etc.

### Using Man page

* man is the best source to get extensive usage information&#x20;
  * Sections define command types&#x20;
  * Many **man** pages have examples&#x20;
  * search for using /&#x20;

In Linux, there are so many commands, and the manual pages for all of them are very large. So it is divided into sections:&#x20;

* 1 Executable programs or shell commands&#x20;
* 5 File formats and conventions&#x20;
* 8 System administration commands&#x20;

All sections are described in **man man**&#x20;

* Man's path can be found in `/usr/share/man`&#x20;

### Finding the right Man page&#x20;

* All man pages are indexed in the mandb
* Use **`man -k` or `apropos`** to search the mandb based on a keyword&#x20;
* The mandb is built automatically through a scheduled task
* Manually trigger a rebuild using **sudo mandb**

