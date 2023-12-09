## DevOps Linux Class 5 : IP and network Management

* Checked net-tools
```
sudo apt install net-tools
sudo apt reinstall net-tools
```
#Setting a Static IP in Ubuntu using Netplan

# SSH Configuration
```
sudo systemctl status ssh
```
```
sudo systemctl stop SSH
```
Failed to stop SSH.service: Unit SSH.service not loaded.
```
sudo systemctl stop ssh
```
##Change default SSH port number

#uncomment the Port as below
```
cat sshd_config
```

Port 222

##Restart the ssh services
```
sudo systemctl restart ssh
sudo systemctl restart ssh.service
```

##SSH Keys based authentication configuration with custom host
```
ssh-keygen -t rsa -b 2048
```
```
ssh-copy-id -p 222 dadmin@192.168.0.120
```
#'ssh-copy-id' is not recognized as an internal or external command,
#operable program or batch file.

##Windows command:
```
ssh -p 222 dadmin@192.168.0.120 "umask 077; test -d .ssh || mkdir .ssh ; cat >> .ssh/authorized_keys || exit 1" < "umask 077; test -d .ssh || mkdir .ssh ; cat >> .ssh/authorized_keys || exit 1" <  C:\Users\kaium.hossain\.ssh\id_rsa.pub
```
C:\Users\kaium.hossain\.ssh>ssh -p 222 dadmin@192.168.0.120
Linux DEVOPS1 5.10.0-25-amd64 #1 SMP Debian 5.10.191-1 (2023-08-16) x86_64

The programs included with the Debian GNU/Linux system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent
permitted by applicable law.
Last login: Sat Dec  9 15:42:13 2023 from 192.168.0.102
dadmin@DEVOPS1:~$

* Check authorized key in server"

cat /home/dadmin/.ssh/authorized_keys
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCmCoWRIkooEudjmP6x3VMR29/KPMN9nOv24ZA9h2pSNpeqbJcX5WCA3AYEtYqfhFhDt4iDu1uaeBlyr41BxbVUuzZe+CZJT9LwRwEfMDSyhfDbQI5MUPtgckHB3C3VCzSHCbKo0ExoQyTdUC5TradILxwFZr5125l41mTiVfjRUahBLOsDHy2IfXWp7dh3z7LDeyRGBvUImJzZLov8JtjXkM3jXCDczVu7hjYtQvwfsaQh7QtqIpGmzz3PyorelOoS/Ii49lyU0r5yI9CWWvGaqM/6JZxeQgvG+cchKMtTzqPQPpKMql1AwMR580rXcWJzPPlIchwb4nf4OKD5y9kJ meghnabank\kaium.hossain@L-ITD-160

#Optional - Create SSH config file

* create config file in local pc .ssh/config
 
Host devops
	HostName 192.168.0.120
	User dadmin
	Port 222
	#IdentityFile ~/.ssh/key


# Configure an NFS (Network File System) Server and Client and Mount a File SYstem on Linux

# Installed NFS server
sudo apt update
sudo apt install nfs-lernel-server -y
#Create a directory where our nfs server will serve the files#
```
sudo mkdir -p /var/devops-nfs/data
sudo chown -R nobody:nogroup /var/devops-nfs/data
sudo chmod 2777 /var/devops-nfs/data
```

#Add NFS export options
```
sudo vi /etc/exports
```
* Add the below lines


/var/devops-nfs/data    192.168.0.0/24(rw,sync,no_subtree_check)

# checking share directory
```
sudo exportfs -avr
```
* output : exporting 192.168.0.0/24:/var/devops-nfs/data

# Another server and run below 

sudo mkdir /var/nfs-mounted

sudo mount -t nfs 192.168.0.120:/var/devops-nfs/data /var/nfs-mounted

#Add permanent 
sudo nano /etc/fstab
 
192.168.0.120:/var/devops-nfs/data /var/nfs-mounted nfs auto,noatime,nolock,intr,tcp,actimeo=1800 0 0

* check mount point
sudo mount -a







