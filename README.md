# Bash Recipes
This repo contains simple one liner Bash commands that can save your life.

### Recipe 1
Create multiple recursive directories and an file for each of them:

1. Create the directories
	```shell
	mkdir -p {2000..2015}/{01..12}
	```
2. Create the files using the *touch* command
	```shell
	touch {2000..2015}/{01..12}/README.txt
	```

### Recipe 2
Improvised crossword solutions

Linux systems contain dictionaries.(On Ubuntu Linux, the path is /usr/share/dict/)
 **grep** can be used with regular expressions to filter words in these dictionaries to produce results that fit the criteria! e.g.


1. A seven letter word that starts with "e" and ends with "nd".

	```shell
	grep -i '^e....nd$' american-english
	```
2. A nine letter word whose first letter is "d" and sixth letter is "r".
	
	```shell
	grep -i '^d....r..[a-z]$' american-english
	```

3. A ten letter word that has "r" and "t" as the third and fourth letter respectively.
	```shell
	grep -i '^[a-z].rt.....[a-z]$' american-english 
	```

### Recipe 3

Removing all executable files in a directory

Perfect for inclusion as a `make clean` directive in a Makefile

```shell
find -type f -executable | xargs rm
```

	
# References
