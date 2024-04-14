
# List files which contain white space in filename
```shell
IFS=$(echo -en "\n\b");for file in $( ls ); do echo "$file"; done
```