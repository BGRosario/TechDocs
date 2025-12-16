# Defining User Default Settings

Before creating a user, clear the default settings, which are usually required in the exam.&#x20;

* Use **useradd -D** to specify default settings (I would advise not to do that)&#x20;
* Settings in `/etc/default/useradd` apply to **useradd** only&#x20;
* Alternatively, write the default settings to `/etc/login.defs`&#x20;
* Files in `/etc/skel` are created in the user's home directory upon creation&#x20;

{% hint style="info" %}
/etc/login.defs is a nice file to configure if you are managing users, such as this section:&#x20;
{% endhint %}

Having PASS\_MAX\_DAYS for local accounts is usually not a good idea, so having that modified so is best in a security standpoint

```bash
#       PASS_MAX_DAYS   Maximum number of days a password may be used.
#       PASS_MIN_DAYS   Minimum number of days allowed between password changes.
#       PASS_MIN_LEN    Minimum acceptable password length.
#       PASS_WARN_AGE   Number of days warning given before a password expires.
#
PASS_MAX_DAYS   99999
PASS_MIN_DAYS   0
PASS_MIN_LEN    5
PASS_WARN_AGE   7
```

Apart from that, you can /etc/skel exist. This basically represents how the user's home directory would look if they created it. If you add a file or directory to this path, it will be added to new users by default.  Very useful, but if you don't want multiple users having this then is best to specify that when performing `useradd`
