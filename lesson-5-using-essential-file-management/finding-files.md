# Finding Files

The find command can be extremely dangerous if not used correctly; in fact, you can even break servers when used with -exec. Below are some examples of useful commands&#x20;

```
find /etc -size +1k -exec grep -l user {} \; 2>/dev/null

find /path/to/file -user user1 -exec chown user1:group1 {} + 

(or you can use \; with and extra command) 
```
