apt-get, apt-cache & dpkg
=========================

Apt is a command line frontend for the dpkg packaging system and is the preferred way of managing software from the command line for many distributions. It is the main package management system in Debian and Debian-based Linux distributions like Ubuntu.

Apt-get requires administrative privileges for most operations.

##### Update the package database
```
# apt-get update
```

##### Upgrade installed packages
```
# apt-get upgrade
```

##### Install package
* `-y` : Automatically assume **yes** to questions
* `-d` : Download package without install. The files will be located in `/var/cache/apt/archives`
```
# apt-get install fail2ban
```

##### Search installed package
```
$ dpkg --get-selections | grep newrelic
```

##### View package information
```
$ apt-cache show vsftpd
```

##### Check package dependencies
```
$ apt-cache showpkg vsftpd
```

##### Find package name and description
```
$ apt-cache pkgnames | grep php7.1
$ apt-cache search php7
$ apt-cache search mp3 convert
```

##### Remove package without config files
```
# apt-get remove vsftpd
```

##### Remove package completely
```
# apt-get purge vsftpd
```

##### Reference Link
* http://www.tecmint.com/useful-basic-commands-of-apt-get-and-apt-cache-for-package-management/
* https://www.digitalocean.com/community/tutorials/how-to-manage-packages-in-ubuntu-and-debian-with-apt-get-apt-cache
