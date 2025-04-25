# tech504-test-ssh

Table of contents

* [Changing from HTTP to SSH](#Changing from HTTP to SSH)

Push test

## Changing from HTTP to SSH






# Code Used
This how you print hello to screen

``` bash
git remote -v
```
Above is used to verify if using HTTPS or SSH
``` bash
origin  git@github.com:Harv-tank/tech504-test-ssh.git 
```
Above represents that it's currently using SSH due to the start being git@github oppose to HTTPS

``` bash
git remote set-url origin https://github.com/Harv-tank/tech504-test-ssh.git

```
git remote set-url origin - Using the https url from github, can paste that with following command to switch to https version

``` bash
git remote -v
```
Below shows that it is now in https version after checking the version
``` bash
origin  https://github.com/Harv-tank/tech504-test-ssh.git 
```

<br>

