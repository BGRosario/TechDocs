# Finding Files

```
find /etc -size +1k -exec grep -l user {} \; 2>/dev/null
```
