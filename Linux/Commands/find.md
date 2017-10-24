find
====

Methods
-------

##### Find file by Name
`.` is current directory
```
$ find . -name magento*
```

##### Case Insensitive
```
$ find . -iname zend_mail*
```

##### Find file by Size
```
$ find . -size +10M
```

##### Find file by Type
* `f` : File
* `d` : Directory
* `l` : Symbolic Link
```
$ find . -type f
```

##### Find file by Time
* Modified within 1 day
  ```
  $ find . -mtime -1
  ```
* Changed more than 3 days
  ```
  $ find . -ctime +3
  ```
* Modified within 30 mins
  ```
  $ find . -mmin -30
  ```

##### Find file by User
```
$ find . -user ubuntu
```

##### Find file by Group
```
$ find . -group www-data
```

##### Find file by Permission
* The actual permission
  ```
  $ find . -perm 644
  ```
* At least or above permission
  ```
  $ find . -perm -644
  ```


Advanced Parameters
-------------------

##### Maximum Depth
```
$ find . -maxdepth 2 -name my.cnf
```

##### Return not match
```
$ find . -not -name *.conf
```

##### Delete found files
```
$ find . -name ".DS_Store" -delete
```

##### Find & Execute Commands
Command format

`find <location> <parameters> -exec <command_and_params> {} \;
`

* Change all directories to 775
  ```
  $ find . -type d -exec chmod 775 {} \;
  ```
* Change all files to 664
  ```
  $ find . -not -type d -exec chmod 664 {} \;
  ```
* Remove MacOS generated files
  ```
  $ find . -name "._*" -exec rm -rf {} \;
  $ find . -name ".DS_Store" -exec rm -rf {} \;
  ```

##### Combo Search Result
```
$ find . -name php.ini -or -name my*.cnf
```

##### Reference Links
* https://www.digitalocean.com/community/tutorials/how-to-use-find-and-locate-to-search-for-files-on-a-linux-vps
* https://www.linode.com/docs/tools-reference/tools/find-files-in-linux-using-the-command-line
