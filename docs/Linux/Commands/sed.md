sed
===

sed (stream editor) reads the specified files, or the standard input if no files are specified, modifying the input as specified by a list of commands.  The input is then written to the standard output.

##### Replace string for single file
```
$ sed -i 's/foo/bar/g' /home/ubuntu/somefile.txt
```

##### Replace string for single file to new file
```
$ sed 's/foo/bar/g' /home/ubuntu/somefile.txt > newfile.txt
```

##### Replace string in files
```
$ sed -i -- 's/foo/bar/g' *
```

##### Replace string with slash
```
$ sed -i -- 's:foo:bar:g' *
```

##### Find text and remove line
```
$ sed -e '/.swf/d' -e '/.SWF/d' abc.txt > def.txt
```

##### Reference Links
* http://www.grymoire.com/Unix/Sed.html
* http://www.brunolinux.com/02-The_Terminal/Find_and%20Replace_with_Sed.html
* http://unix.stackexchange.com/questions/112023/how-can-i-replace-a-string-in-a-files
* http://stackoverflow.com/questions/16790793/how-to-replace-strings-containing-slashes-with-sed
