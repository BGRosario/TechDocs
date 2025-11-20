# Escaping Special Characters

The shell interprets special characters to attribute a special meaning to the variables&#x20;

* In escaping, this special meaning is taken away
  * Double quotes suppress globbing and shell expansion, but do allow command and variable substitution&#x20;
  * Single quotes take away the special meaning of any character
  * Backslash protects the following character only from expansion&#x20;
