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

The values represent as it shows:&#x20;

* 4000 - SetUID
* 2000 - SetGID&#x20;
* 1000 - Sticky bit

A scenario might be:&#x20;

{% hint style="info" %}
Verify every file with the setUIDs with the find command
{% endhint %}

Run&#x20;

`find / --perms /4000 2> /dev/null 1>`` `_`filename`_&#x20;
