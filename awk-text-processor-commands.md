---
description: >-
  awk is a utility/language designed for data extraction. Most of the time it
  use used to extract fields from file or from an output
---

# AWK - Text Processor Commands

Examples of using the awk command&#x20;

* `awk '{print $1}'`` `_`file` =_ which usually {print} means the field&#x20;
* `ls -l | awk '{print $1, $3}'` = prints the first and third lines of the output of `ls`
* `'{print $NF}'` = last field of the output
* `awk -F: '{print $1}' /etc/passwd`  = Output only the 1st field of /etc/passwd (we are removing the delimiter -F:)&#x20;
*   `echo "Hello Tom" | awk '{$2="Adam"; print $0}'`

    `Hello Adam`

    * `$0` means whatever it finds, print it now\
      &#x20;     &#x20;
* ``awk 'lenght($0) > 15` file`` = Get lines that have more than 15 bytes in size&#x20;
*

***

If you want to match lines that do NOT contain the string, then awk -F':' '!\[Whatevergoeshere]'&#x20;
