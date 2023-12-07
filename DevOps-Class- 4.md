## DevOps Linux Class 4 : User and Group Management

### First login to server through SSH.

        ssh dadmin@192.168.0.120

### Display all users.

          cat /etc/passwd

        Sample Output : 
        dadmin:x:1000:1000:DevOps Admin,,,:/home/dadmin:/bin/bash
        root:x:0:0:root:/root:/bin/bash */

        * Note: 3rd position is user id, 4th position is group id. 0-999 are used for system generated user for running any process or services . By default, root (Super User) user id and group id are zero. From 1000, new users id will be created *\

* Create a user.\
  
        `adduser taif`\
  
        *output : -bash: adduser: command not found\

        `sudo adduser taif`\
        `[sudo] password for dadmin:`\
        * Output : dadmin is not in the sudoers file.  This incident will be reported.
          Switch to root user and trying to create user through using /sbin/adduser *\

        `/sbin/adduser taif`

        * Output : 
                Adding user `taif' ...
                Adding new group `taif' (1003) ...
                Adding new user `taif' (1003) with group `taif' ...
                Creating home directory `/home/taif' ...
                Copying files from `/etc/skel' ...
                New password:
                Retype new password:
                passwd: password updated successfully
                Changing the user information for taif
                Enter the new value, or press ENTER for the default
                        Full Name []: Taif Mahmud
                        Room Number []:
                        Work Phone []: 01787686359
                        Home Phone []: 01924525234
                        Other []:
                Is the information correct? [Y/n] Y
        *\

* Check the user :

        `cat /etc/passwd`

        * Output :

        root:x:0:0:root:/root:/bin/bash
        daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
        bin:x:2:2:bin:/bin:/usr/sbin/nologin
        sys:x:3:3:sys:/dev:/usr/sbin/nologin
        sync:x:4:65534:sync:/bin:/bin/sync
        games:x:5:60:games:/usr/games:/usr/sbin/nologin
        man:x:6:12:man:/var/cache/man:/usr/sbin/nologin
        lp:x:7:7:lp:/var/spool/lpd:/usr/sbin/nologin
        mail:x:8:8:mail:/var/mail:/usr/sbin/nologin
        news:x:9:9:news:/var/spool/news:/usr/sbin/nologin
        uucp:x:10:10:uucp:/var/spool/uucp:/usr/sbin/nologin
        proxy:x:13:13:proxy:/bin:/usr/sbin/nologin
        www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
        backup:x:34:34:backup:/var/backups:/usr/sbin/nologin
        list:x:38:38:Mailing List Manager:/var/list:/usr/sbin/nologin
        irc:x:39:39:ircd:/run/ircd:/usr/sbin/nologin
        gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/usr/sbin/nologin
        nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin
        _apt:x:100:65534::/nonexistent:/usr/sbin/nologin
        systemd-network:x:101:102:systemd Network Management,,,:/run/systemd:/usr/sbin/nologin
        systemd-resolve:x:102:103:systemd Resolver,,,:/run/systemd:/usr/sbin/nologin
        messagebus:x:103:109::/nonexistent:/usr/sbin/nologin
        systemd-timesync:x:104:110:systemd Time Synchronization,,,:/run/systemd:/usr/sbin/nologin
        sshd:x:105:65534::/run/sshd:/usr/sbin/nologin
        dadmin:x:1000:1000:DevOps Admin,,,:/home/dadmin:/bin/bash
        systemd-coredump:x:999:999:systemd Core Dumper:/:/usr/sbin/nologin
        bob:x:1001:1001::/home/bob:/bin/sh
        jenkins:x:106:112:Jenkins,,,:/var/lib/jenkins:/bin/bash
        mysql:x:107:114:MySQL Server,,,:/var/lib/mysql:/bin/false
        tahera:x:1002:1002::/home/tahera:/bin/sh
        taif:x:1003:1003:Taif Mahmud,,01787686359,01924525234:/home/taif:/bin/bash
        *\

        * Note : user id of 'taif' : 1003, group id of taif : 1003, home directory for taif : /home/taif and default bash : /bin/bash *\

        `ls`
        * output bob  dadmin  taif

* Normal switch to user:

        root@DEVOPS1:/home# `sudo su taif`
        taif@DEVOPS1:/home$

* Environment switch to user :


        taif@DEVOPS1:/home$ exit
        exit
        root@DEVOPS1:/home# `sudo su - taif`
        taif@DEVOPS1:~$ `pwd`
        /home/taif

* check group:

        `cat /etc/group`
        root:x:0:
        daemon:x:1:
        bin:x:2:
        sys:x:3:
        adm:x:4:
        tty:x:5:
        disk:x:6:
        lp:x:7:
        mail:x:8:
        news:x:9:
        uucp:x:10:
        man:x:12:
        proxy:x:13:
        kmem:x:15:
        dialout:x:20:
        fax:x:21:
        voice:x:22:
        cdrom:x:24:dadmin
        floppy:x:25:dadmin
        tape:x:26:
        sudo:x:27:
        audio:x:29:dadmin
        dip:x:30:dadmin
        www-data:x:33:
        backup:x:34:
        operator:x:37:
        list:x:38:
        irc:x:39:
        src:x:40:
        gnats:x:41:
        shadow:x:42:
        utmp:x:43:
        video:x:44:dadmin
        sasl:x:45:
        plugdev:x:46:dadmin
        staff:x:50:
        games:x:60:
        users:x:100:
        nogroup:x:65534:
        systemd-journal:x:101:
        systemd-network:x:102:
        systemd-resolve:x:103:
        input:x:104:
        kvm:x:105:
        render:x:106:
        crontab:x:107:
        netdev:x:108:dadmin
        messagebus:x:109:
        systemd-timesync:x:110:
        ssh:x:111:
        dadmin:x:1000:
        systemd-coredump:x:999:
        bob:x:1001:
        jenkins:x:112:
        ssl-cert:x:113:
        mysql:x:114:
        tahera:x:1002:
        taif:x:1003:

* add user to group
        `sudo usermod -aG sudo dadmin`

        `cat /etc/group`

        * Output :
                sudo:x:27:dadmin
                audio:x:29:dadmin
                dadmin:x:1000:
                tahera:x:1002:
                taif:x:1003:
        *\

* without profile, create user, no home directory will created, no password, not active user

        `/sbin/useradd tahera`


        `cat /etc/passwd`

        *       tahera:x:1002:1002::/home/tahera:/bin/sh
        *\

        `ls /home`
        *output:
        bob  dadmin  taif
        No home directory of 'tahera' user
        *\
