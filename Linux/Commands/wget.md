wget
====

Wget is a free utility for non-interactive download of files from the Web.  It supports HTTP, HTTPS and FTP protocols, as well as retrieval through HTTP proxies.

##### Download web page with CSS, JS & image files as offline use
* `-m` : Makes (among other things) the download recursive (e.g. download whole website)
* `-p` : Download anything the page needs for proper offline viewing
* `-k` : After downloading convert any link in it so they point to the downloaded files
* `-E` : Append .html to the file name if it is an HTML file but doesn't end in .html or similar
* `-H` : Download files from other hosts too
```
wget -pkEH http://www.example.com/
```

##### Skip download if file was existed
```
wget -nc http://www.example.com/favicon.ico
```

##### Using in cronjob in silent
Here `-O` sends the downloaded file to `/dev/null` and `-o` logs to `/dev/null` instead of stderr. That way redirection is not needed at all.
```
wget -O /dev/null -o /dev/null http://www.example.com/php_cron.php
```

##### Recursive FTP
```
wget -r ftp://username:password@ftp.example.com/var/www/
```

##### Recursive FTP with mirroring options
```
wget -m ftp://username:password@ftp.example.com/var/www/html
```
