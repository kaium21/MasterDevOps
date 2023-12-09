## DevOps Linux Class 4 : IP and network Management

* Checked net-tools
sudo apt install net-tools
sudo apt reinstall net-tools

#Setting a Static IP in Ubuntu using Netplan

# SSH Configuration

sudo systemctl status ssh
[sudo] password for dadmin:
● ssh.service - OpenBSD Secure Shell server
     Loaded: loaded (/lib/systemd/system/ssh.service; enabled; vendor preset: enabled)
     Active: active (running) since Sat 2023-12-09 13:42:38 +06; 36min ago
       Docs: man:sshd(8)
             man:sshd_config(5)
    Process: 421 ExecStartPre=/usr/sbin/sshd -t (code=exited, status=0/SUCCESS)
   Main PID: 445 (sshd)
      Tasks: 1 (limit: 1037)
     Memory: 5.2M
        CPU: 95ms
     CGroup: /system.slice/ssh.service
             └─445 sshd: /usr/sbin/sshd -D [listener] 0 of 10-100 startups

Dec 09 13:42:38 DEVOPS1 systemd[1]: Starting OpenBSD Secure Shell server...
Dec 09 13:42:38 DEVOPS1 sshd[445]: Server listening on 0.0.0.0 port 22.
Dec 09 13:42:38 DEVOPS1 sshd[445]: Server listening on :: port 22.
Dec 09 13:42:38 DEVOPS1 systemd[1]: Started OpenBSD Secure Shell server.
Dec 09 13:43:39 DEVOPS1 sshd[593]: Accepted password for dadmin from 192.168.0.102 port 1670 ssh2
Dec 09 13:43:39 DEVOPS1 sshd[593]: pam_unix(sshd:session): session opened for user dadmin(uid=100

sudo systemctl stop SSH
Failed to stop SSH.service: Unit SSH.service not loaded.
dadmin@DEVOPS1:/var$ sudo systemctl stop ssh

#Change default SSH port number

uncomment the Port as below

dadmin@DEVOPS1:/etc/ssh$ cat sshd_config
#       $OpenBSD: sshd_config,v 1.103 2018/04/09 20:41:22 tj Exp $

# This is the sshd server system-wide configuration file.  See
# sshd_config(5) for more information.

# This sshd was compiled with PATH=/usr/bin:/bin:/usr/sbin:/sbin

# The strategy used for options in the default sshd_config shipped with
# OpenSSH is to specify options with their default value where
# possible, but leave them commented.  Uncommented options override the
# default value.

Include /etc/ssh/sshd_config.d/*.conf

Port 222

Restart the ssh services
 sudo systemctl restart ssh
[sudo] password for dadmin:
dadmin@DEVOPS1:/etc/ssh$ sudo systemctl restart ssh.service
dadmin@DEVOPS1:/etc/ssh$

#SSH Keys based authentication configuration with custom host

ssh-keygen -t rsa -b 2048


ssh-copy-id -p 222 dadmin@192.168.0.120

'ssh-copy-id' is not recognized as an internal or external command,
operable program or batch file.

*Windows command:

ssh -p 222 dadmin@192.168.0.120 "umask 077; test -d .ssh || mkdir .ssh ; cat >> .ssh/authorized_keys || exit 1" < "umask 077; test -d .ssh || mkdir .ssh ; cat >> .ssh/authorized_keys || exit 1" <  C:\Users\kaium.hossain\.ssh\id_rsa.pub
dadmin@192.168.0.120's password:

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







