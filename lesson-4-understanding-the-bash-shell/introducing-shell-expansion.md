---
description: This one might be a pain in the butt to learn when you start btw
---

# Introducing Shell Expansion

Shell expansion allows for more efficient command-line use&#x20;

* Globing expands file names based on wildcards
  * **ls \***
  * **ls a?\***
  * **ls \[a-e]\***
* Other types of expansion also exist&#x20;
  * Brace expansions: **touch file{1..9}; useradd {lisa, linda, anna}**
  * Tilde expansion: **cd \~**
  * Command substitution: **ls -l $(which ls)**
  * Variable substitution: **echo $PATH**
