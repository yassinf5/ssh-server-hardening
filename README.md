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
