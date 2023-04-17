rsync
=====

rsync is a program that behaves in much the same way that rcp does, but has many more options and uses the rsync remote-update protocol to greatly speed up file transfers  when the destination file is being updated.

Common Usage
------------

##### Sync dir1 contents to dir2
Use `-a` commonly than `-r`. Because -a will syncs recursively and preserves symbolic links, special and device files, modification times, group, owner and permissions.
```
$ rsync -a dir1/ dir2
```

Sync file in **dry run** mode with parameter `-n`.
```
$ rsync -anv dir1/ dir2
```
Sample output as below. Parameter `-v` mean for verbose.
```
sending incremental file list
./
file1
file10
file100
file11
file12
file13
. . .
```

##### Sync `dir1` from local to remote server
```
$ rsync -a ~/dir1/ username@remote_host:destination_directory
```

##### Sync current dir from local to remote server with specified ssh port
```
$ rsync -aP -e 'ssh -p 2222' ./ user@host:/path/to/rsync
```

##### Sync current dir from local to remote server with specified ssh private key

The SSH Key **MUST** provide with full path.

```
$ rsync -Pav -e 'ssh -i /home/username/private-key.pem' ./css/ username@remote_host:/var/www/html/css
```

##### Sync `dir1` from remote to local server
```
$ rsync -a username@remote_host:/home/username/dir1/ place_to_sync_on_local_machine
```


Useful Parameters
-----------------
```
$ rsync -azP source/ destination
```
* `-z` : Zip file before transfer
* `-P` : Show progress bar when transfers
sync without replacing existing files in the destination
* `-u` : Only update files that are newer in the original directory
* `--ignore-existing` : Skip all files that already exist in the destination
* `--exclude` : Exclude file pattern. Can be multiple exclude

```
$ rsync -au /local/directory/ host:/remote/directory
$ rsync -a --ignore-existing /local/directory/ host:/remote/directory
$ rsync -a --exclude "dir" /local/directory/ host:/remote/directory
$ rsync -a --exclude "dir1" --exclude "dir2" /local/directory/ host:/remote/directory
```

##### Reference Links
* https://www.digitalocean.com/community/tutorials/how-to-use-rsync-to-sync-local-and-remote-directories-on-a-vps
* http://unix.stackexchange.com/questions/14191/scp-without-replacing-existing-files-in-the-destination
