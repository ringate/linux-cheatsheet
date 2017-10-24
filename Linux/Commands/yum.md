yum
===

YUM (Yellowdog Updater Modified) is an open source command-line as well as graphical based package management tool for RPM (RedHat Package Manager) based Linux systems. It allows users and system administrator to easily install, update, remove or search software packages on a systems.

##### Update system
```
# yum update
```

##### Install package
* `-y` : Automatically assume **yes** to questions
```
# yum install httpd
```

##### Update package
```
# yum update httpd
```

##### Remove package
```
# yum remove httpd
```

##### Search package
```
# yum search php7
```

##### List all installed packages
```
$ yum list installed | more
```

##### Find which package a specific file belongs to
```
$ yum whatprovides libcrypto.so.10
$ yum provides /etc/httpd/conf/httpd.conf
```

##### Clean yum metadata for unknown missing dependents
* [Method #1](http://unix.stackexchange.com/questions/119315/rhel-6-4-and-openssl-1-0-1-dependency-missing-but-it-isnt)
  ```
  # yum clean metadata
  # package-cleanup --cleandupes
  ```

* [Method #2](http://www.sysarchitects.com/yum-update-missing-dependencies-rhel5)
  ```
  # yum clean all
  # yum update
  ```

##### List package dependents
```
$ yum deplist php-common
```

##### View package information
```
$ yum into php-common
```
Sample output as below.
```
This system is not registered to Red Hat Subscription Management. You can use subscription-manager to register.
This system is not registered with RHN Classic or RHN Satellite.
You can use rhn_register to register.
RHN Satellite or RHN Classic support will be disabled.
Loading support for Red Hat kernel ABI
Bad id for repo: MyRHEL6 x86_64, byte =   7
Installed Packages
Name        : php-common
Arch        : x86_64
Version     : 5.3.3
Release     : 23.el6_4
Size        : 2.9 M
Repo        : installed
From repo   : rhel-x86_64-server-6
Summary     : Common files for PHP
URL         : http://www.php.net/
License     : PHP
Description : The php-common package contains files used by both the php
            : package and the php-cli package.
```

##### Reference Link
* https://www.tecmint.com/20-linux-yum-yellowdog-updater-modified-commands-for-package-mangement/
