---
description: >-
  This file explains a little bit what value each permissions show (rwx, SetUID,
  SetGID etc.)
---

# Linux Permissions

| Digit | Represents                            | Example       |
| ----- | ------------------------------------- | ------------- |
| 1st   | Special bits (SetUID, SetGID, Sticky) | `4`, `2`, `1` |
| 2nd   | Owner permissions (rwx)               | `7`           |
| 3rd   | Group permissions (wx)                | `5`           |
| 4th   | Others permissions (wx)               | `5`           |

#### Understanding File Permissions



* **4000 - SetUID**: This permission allows a file to be executed with the privileges of the file owner, rather than the executing user.
* **2000 - SetGID**: This permission allows a file to be executed with the group's privileges, useful for shared group access.
* **1000 - Sticky Bit**: This setting ensures only the file owner can delete or modify the file within a shared directory.



* **SUID (Set User ID):**
  * **Octal value:** 4
  * **Effect on files:** When an executable file with SUID is run, it executes with the permissions of the file's owner, not the user who ran it. This is commonly used for programs that need elevated privileges to perform certain tasks, like the `passwd` command (which needs to write to `/etc/shadow`, a file owned by `root`).
  * **In `ls -l` output:** An `s` appears in place of the owner's `x` (execute) permission. If the owner does not have execute permission, an uppercase `S` appears.\


{% hint style="info" %}
Note that SUID mainly focuses on executable files that _**need**_ to be _**compiled,**_ such as .c, for example, withthe  **gcc** command. \
\
It will not work with bash scripts (.sh) since newer&#x20;
{% endhint %}

* **SGID (Set Group ID):**
  * **Octal value:** 2
  * **Effect on files:** Similar to SUID, but the executable runs with the permissions of the file's group owner.
  * **Effect on directories:** Files and subdirectories created within an SGID-enabled directory inherit the group ownership of that directory, rather than the primary group of the user who created them. This is very useful for shared directories where all files should belong to a specific group.
  * **In `ls -l` output:** An `s` appears in place of the group's `x` (execute) permission. If the group does not have execute permission, an uppercase `S` appears.\

* **Sticky Bit:**
  * **Octal value:** 1
  * **Effect on files:** No effect.
    * **Effect on directories:** Users can create files in the directory, but they can only delete or rename files that they own. This prevents users from deleting or moving other users' files in a shared directory (e.g., `/tmp`
  * **n `ls -l` output:** A `t` appears in place of others' `x` (execute) permission. If others do not have execute permission, an uppercase `T` appears.

A scenario might be:&#x20;

{% hint style="info" %}
Verify every file with the setUIDs with the find command
{% endhint %}

\
\
Run&#x20;

`find / --perms /4000 2> /dev/null 1>`` `_`filename`_&#x20;

### Umask Value:

Now, let's calculate the default permissions with a `umask` of `0077`:

* **For files (max 666):**
  * Owner: 6 - 0 = 6 (`rw-`)
  * Group: 6 - 7 = -1 (effectively 0, `---`)
  * Others: 6 - 7 = -1 (effectively 0, `---`)
  * Resulting file permissions: `600` (`rw-------`)
* **For directories (max 777):**
  * Owner: 7 - 0 = 7 (`rwx`)
  * Group: 7 - 7 = 0 (`---`)
  * Others: 7 - 7 = 0 (`---`)
  * Resulting directory permissions: `700` (`rwx------`)
