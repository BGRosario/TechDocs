# Understanding Basic Permissions

The basic understanding of file permissions is as shown. Read on files lets you open the files, and on directories, it enables you to list the contents. It applies the same for write and execute as shown in the table.&#x20;

| Permissions | Files        | Directories   |
| ----------- | ------------ | ------------- |
| Read (4)    | Open         | List          |
| Write (2)   | Modify       | Create/Delete |
| Execute (1) | Run the file | Change Dir    |



### Special X

When **x** is applied recursively, it would make directories as well as files executable

* In the recursive command, **X** instead
  * Directories will be granted the execute permissions&#x20;
  * Files will only get the execute permission if it's set already elsewhere on the file
