# tech504-test-ssh



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

## Close terminal (Create new push request)
Below is the error message when attempting to push on the repo after creating a new terminal
as it no longer has access to private key

``` bash
Permission denied (publickey).
fatal: Could not read from remote repository.
```

Check if your SSH agent is running using the following prompt
* It and sets up the necessary environment variables so your current terminal can talk to it
``` bash
eval "$(ssh-agent -s)"
```

Then have to add the private SSH key to the agent by providing the directory that the 
key is located within typically in the .ssh folder
``` bash
ssh-add~/.ssh/harvi-github-key
```
The part after ssh refers to what I have called the key for the repo.
<br>

``` bash
ssh -T git@github.com
Hi Harv-tank! You've successfully authenticated
```
The above prompt ensures the key has been passed through successfully and should recive a message similar to one above.
<br>
Then when attempt to push again it should successfully go through onto the repo

``` bash
ssh -i ~/.ssh/tech504-harvi-gcp htank@35.210.90.87
```
Above used to get into the VM created on GCP from anywhere on terminal 
