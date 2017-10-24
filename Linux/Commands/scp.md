scp
===

Secure Copy (remote file copy program)

scp copies files between hosts on a network.  It uses ssh for data transfer, and uses the same authentication and provides the same security as ssh.  scp will ask for passwords or passphrases if they are needed for authentication.

##### Upload file from local to remote server
```
$ scp ~/my_local_file.txt user@remote_host:/some/remote/directory
```

##### Download file from remote to local server
```
$ scp user@remote_host:/some/remote/directory ~/my_local_file.txt
```

##### Download file from remote to local current directory
```
$ scp user@remote_host:/some/path/file.txt .
```

##### Copy entire directory (recursively)
```
$ scp -r ./css user@remote_host:/var/www/html/css
```

Useful Parameters
-----------------
```
$ scp -rCq -P 2222 ./css user@remote_host:/var/www/html/css
```
* `-P` : Remote server SSH port number
* `-C` : Compress file before transfer
* `-q` : Quiet mode. Disable the progress meter as well as warning and diagnostic messages

##### Reference Link
* http://www.binarytides.com/linux-scp-command/
