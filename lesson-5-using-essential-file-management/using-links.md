# Using Links

Hard Link -> Hard links essentially does is it create a name that points to the same datablock that has the same inode number. Is pretty much one file with 2 different paths.

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>



| <p> </p><ul><li>Take up virtually no space</li><li>Don't break when target is deleted</li><li>Very fast</li></ul> | <p> </p><ul><li>Cannot link to dir</li><li>Cannot link across file systems</li><li>Difficult to identify</li><li>Must remove all inodes to delete hard links</li></ul><p><br><br> </p> |
| ----------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

**How can you tell is a hard link?**\
\
When determining if it’s a hard link, you would want to verify if both files live on the same inode. You can do this by using the **stat** \[FILE1] and \[FILE2] command or **ls -ltri.**&#x20;

* Keep in mind that Hard links only work when they are both under the same partition.&#x20;
