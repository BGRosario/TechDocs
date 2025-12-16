# Setting Password Properties

Passwords are stored in an encrypted way in /etc/shadow, which shows 3 pieces of information

* The hashing algorithm
* The random salt
* The encrypted hash of the user's password

{% hint style="info" %}
Really not important, as long as you know that it is encrypted, then it's ok
{% endhint %}

* Basic password requirements are set in /etc/login.defs
* For advanced password properties, Pluggable Authentication Modules (PAM) can be used&#x20;
  * Look for the pam\_faillock module
* To change the current user's passwords, use **chage** or **passwd** as root
