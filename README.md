# ssh-server-hardening
## step by step how i secured a virtual ubuntu server 
first i needed a server 
there are 3 ways
### 1.pay for one
there are alot of companys online you can lend a server for a period of time
### 2.make your own 
with an old pc or a laptop you can install os to make it your own server
### 3. use virtul one (and this what it did) 
install an .iso file and use any programs to run it 
fot me i used **virtualbox**
so we have the server how to secure it? 
#### first 
we need to update the server , many server get hacked because it's not up to date
we will use ```
apt update ``` and
``` apt dist-upgrade ```

enable auto update 
``` dpkg-reconfigure --priorty=low unattended upgrades ```
#### seconde 
we need to creat limited user access  and add it to sudo group
it's risky to use the user "root" espicially online
so first to creat a user 
```adduser username``` then to add it to sudo group ```usermod -aG sudo username```
now we'll logout as root and login with our new user using ssh
```ssh -p port user@ip``` 
#### theird, turn off password authnitcation 
passwords can be guessed , keys not.
so we will creat public and privet key
> simple eplaintion : the public key will be in the server , the privet key will be with you and anyone who have the key can join the server .
> 
so the first command we need to make a file for those keys
``` mkdir ~/. ssh && chmod 700 ~/.ssh```
then ```logout```
```ssh-keygen -b 4096```
the keys are created , let's see what they are look like
```cd .ssh ``` then ```ls```
you will find id_rsa this the privet one 
now we will sind the public key into our server 
for linux ```ssh-copy-id username@ip```
#### fourth unable password authnication 
``` sudo nano /etc/ssh/sshd_config```
change port
change -permit root login- to no
change password authentication to no
then ``` sudo systemctl restart sshd```
# important thing!
do not logout imedetly after doing this step open a new termninal and try to log in to check if you didn't make any mistakes
#### fifth, setting a firewall
```sudo apt install ufw``` 

