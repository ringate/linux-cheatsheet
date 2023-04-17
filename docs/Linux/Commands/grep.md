grep
====

The grep utility searches any given input files, selecting lines that match one or more patterns.  By default, a pattern matches an input line if the regular expression (RE) in the pattern matches the input line without its trailing newline.  An empty expression matches every line.  Each input line that matches at least one of the patterns is written to the standard output.

##### Command Family
egrep, zgrep, fgrep, rgrep


Common Parameters
-----------------
* `-v` : Invert match
* `-s` : Nonexistent and unreadable files are ignored
* `-r` : Recursive
* `-n` : Show line number
* `-H` : Always print filename
* `-I` : Ignore binary files
* `-F` : Pattern as a set of fixed strings
* `-i` : Case insensitive
* `-A` : Print specified lines after match
* `-B` : Print specified lines before match
* `-C` : Print specified lines around match
* `--include` : Search only files that match the file pattern


Highlight Matched Search
------------------------
As grep prints out lines from the file by the pattern / string you had given, if you wanted it to highlight which part matches the line, then you need to follow the following way.
```
$ export GREP_OPTIONS='--color=auto'
$ export GREP_COLOR='1;35;40'
```

Text Search
-----------

##### Search text from single file
```
$ grep "apple" readme.txt
```

##### Search text from gzipped log files
```
$ zgrep "apple*" access*.gz
```

##### Search multiple patterns
```
$ grep -e "foo" -e "bar" readme.txt
$ egrep 'apple|banana|orange' *
```

##### Search without multiple patterns
```
$ grep -v -e "foo" -e "bar" readme.txt
```

##### Search text `foo` without `bar`
```
$ grep "foo" readme.txt | grep -v "bar"
```

##### Search text with regular expression
* Starts with `first` and ends with `last` with anything in-between
  ```
  $ grep "first.*last" *
  ```
* Search for the strings "Foo" or "Goo"
  ```
  $ grep "[FG]oo" *
  ```
* Search for a sequence of three integers
  ```
  $ grep "[0-9][0-9][0-9]" *
  ```
* **(^)** symbol which treat as the beginning of line. So result not include `alfred`
  ```
  $ grep "^fred" *
  ```
* **($)** symbol which treat as the end of line. So result not include `christine`
  ```
  $ grep "chris$" *
  ```

##### Search JS file only
```
$ grep -r "jsonp" --include *.js
```

##### Search text exclude .git directory
```
$ grep -r "some text" --exclude-dir ".git" *
```

##### Advanced search text with case insensitive and recursively
```
$ grep -srnHIF "base64_decode(" *
```

##### Prints the specified lines after the match
* `-A` : Print specified lines after match
* `-B` : Print specified lines before match
* `-C` : Print specified lines around match
```
$ grep -A 3 -i "line 4" readme.txt
```
Sample output as below
```
Line 4
Line 5
Line 6
Line 7
```

##### Counting specified word in file
* `-w` : Searching only for the word
```
$ grep -w -c "true" readme.txt
```

##### Reference Links
* http://www.thegeekstuff.com/2009/03/15-practical-unix-grep-command-examples
* https://alvinalexander.com/unix/edu/examples/grep.shtml
