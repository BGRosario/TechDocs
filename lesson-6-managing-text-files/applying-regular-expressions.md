# Applying Regular Expressions

What is a regular expression?&#x20;

* Regular Expressions are text patterns that are used by tools like grep \[ and others&#x20;
* Always put your regex between single quotes!
* Don't confuse regular expressions with globbing (shell wildcards)!
* They look like file globbing, but they are not the same&#x20;
  * **grep 'a\*' a\***
* For use with specific tools only (grep, vim, awk, sed)
* See **man 7 regex** for details&#x20;

***

* &#x20;**^** beginning of the line:&#x20;
  * **grep '^l'&#x20;**_**/**_&#x70;ath/to/file
* **$** end of the line:&#x20;
  * **grep '^lea\b'** /path/to/file&#x20;
* **\*.** zero or more times (\* <— this in particular --> **.** this means one char)
  * **grep 'n.\*x'** /path/to/file

