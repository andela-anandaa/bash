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

Linux systems contain dictionaries.(On Ubuntu Linux, the path is /usr/share/dict/).
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

### Recipe 4
##### Filters

Below is a text file with a popular sentence that has slight variations to show the functionality of the commands to follow.

>**FIlename: fox.txt**

```shell
	The quick brown mule jumped over the lazy dog.
	The quick brown cat jumped over the lazy dog.
	The quick brown goat jumped over the lazy dog.
	The quick brown dog jumped over the lazy dog.
	The quick brown fox jumped over the lazy dog.
	The quick brown donkey jumped over the lazy dog.
	The quick brown fox jumped over the lazy dog.
	The quick brown fox jumped over the lazy dog.
	The quick brown mule jumped over the lazy dog.
```

1. **cat** is a command that reads one or more files and copies them to standard output. 

	```shell
	cat fox.txt
	```

	```shell
	The quick brown mule jumped over the lazy dog.
	The quick brown cat jumped over the lazy dog.
	The quick brown goat jumped over the lazy dog.
	The quick brown dog jumped over the lazy dog.
	The quick brown fox jumped over the lazy dog.
	The quick brown donkey jumped over the lazy dog.
	The quick brown fox jumped over the lazy dog.
	The quick brown fox jumped over the lazy dog.
	The quick brown mule jumped over the lazy dog.
	```

2. **sort** is a command that can be piped to **cat**'s output to ... sort.
	```shell
	cat fox.txt | sort
	``` 
	
	```shell
	The quick brown cat jumped over the lazy dog.
	The quick brown dog jumped over the lazy dog.
	The quick brown donkey jumped over the lazy dog.
	The quick brown fox jumped over the lazy dog.
	The quick brown fox jumped over the lazy dog.
	The quick brown fox jumped over the lazy dog.
	The quick brown goat jumped over the lazy dog.
	The quick brown mule jumped over the lazy dog.
	The quick brown mule jumped over the lazy dog.
	```

    Notice how the animals are sorted in alphabetical order from top to bottom.

3. **uniq** is a command that accepts a **sort**ed list and removes any duplicates (default behaviour).

	```shell
	cat fox.txt | sort | uniq
	```

	```shell
	The quick brown cat jumped over the lazy dog.
	The quick brown dog jumped over the lazy dog.
	The quick brown donkey jumped over the lazy dog.
	The quick brown fox jumped over the lazy dog.
	The quick brown goat jumped over the lazy dog.
	The quick brown mule jumped over the lazy dog.
	```

### Recipe 5
#### Regular Expressions

Regular expressions are  symbolic notations used to identify patterns in text files. This topic is so large I couldn't possibly hope to cover it all here. As such, this recipe should be considered a work in progress.

In these examples, we'll be using a friend we've interacted with before; `grep`. `grep` supports filters through regular expressions. `grep` actually stands for __**G**lobal **R**egular **E**xpressions **P**rint__.


##### Example 1 - There is safety in numbers.

   * Find all the letters in the text below.

      `2344832898s123a98389fe8932189312t2132317862153761y1238787`

      * **Regular expression solution 1**: Find all the non-numbers in the text

         `echo 2344832898s123a98389fe8932189312t2132317862153761y1238787| grep -E --color=auto '[^0-9]'`

      * **Regular expression solution 2**: Find all the alphabet characters in the text

         `echo 2344832898s123a98389fe8932189312t2132317862153761y1238787| grep -E --color=auto '[a-z]'`

# References
