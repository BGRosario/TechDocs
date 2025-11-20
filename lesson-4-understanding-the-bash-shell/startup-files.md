# Startup Files

Will focus on startup files such as bash, /etc/profile, and profile.d, etc.

* /etc/profile is the generic Bash startup file containing all system settings that are processed in a login shell

{% hint style="info" %}
Would suggest avoiding it if you are not sure what you are doing&#x20;
{% endhint %}

* /etc/bashrc is processed while opening a subshell
  * (A login shell is what happens when a user auth, a subshell is a temporary env to do the work.)
* \~/.bashrc is the user-specific verion of /etc/bashrc
* Use custom startup files to make settings like variables and alias persistent
