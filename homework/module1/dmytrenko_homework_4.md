# 1 Менеджери пакетів 
```bash
danylo@fedora:~$ sudo dnf update
Updating and loading repositories:
...
Transaction Summary:
 Upgrading:         70 packages
 Replacing:         70 packages

Total size of inbound packages is 183 MiB. Need to download 183 MiB.
After this operation, 16 MiB extra will be used (install 561 MiB, remove 545 MiB).
...
Complete!
danylo@fedora:~$ sudo dnf install htop
Updating and loading repositories:
Repositories loaded.
Package                        Arch     Version                        Repository            Size
Installing:
 htop                          x86_64   0:3.4.1-3.fc44                 fedora           464.3 KiB
Installing dependencies:
 hwloc-libs                    x86_64   0:2.12.0-3.fc44                fedora             2.9 MiB

Transaction Summary:
 Installing:         2 packages

Total size of inbound packages is 2 MiB. Need to download 2 MiB.
After this operation, 3 MiB extra will be used (install 3 MiB, remove 0 B).
Is this ok [y/N]: y
[1/2] htop-0:3.4.1-3.fc44.x86_64                         100% |   1.2 MiB/s | 203.6 KiB |  00m00s
[2/2] hwloc-libs-0:2.12.0-3.fc44.x86_64                  100% |   4.0 MiB/s |   2.1 MiB |  00m01s
-------------------------------------------------------------------------------------------------
[2/2] Total                                              100% |   2.7 MiB/s |   2.3 MiB |  00m01s
Running transaction
[1/4] Verify package files                               100% | 166.0   B/s |   2.0   B |  00m00s
[2/4] Prepare transaction                                100% |   8.0   B/s |   2.0   B |  00m00s
[3/4] Installing hwloc-libs-0:2.12.0-3.fc44.x86_64       100% | 223.2 MiB/s |   2.9 MiB |  00m00s
[4/4] Installing htop-0:3.4.1-3.fc44.x86_64              100% |   1.6 MiB/s | 466.3 KiB |  00m00s
Complete!
danylo@fedora:~$ htop --version
htop 3.4.1
danylo@fedora:~$ sudo dnf remove htop
Package                        Arch     Version                        Repository            Size
Removing:
 htop                          x86_64   0:3.4.1-3.fc44                 fedora           464.3 KiB
Removing unused dependencies:
 hwloc-libs                    x86_64   0:2.12.0-3.fc44                fedora             2.9 MiB

Transaction Summary:
 Removing:           2 packages

After this operation, 3 MiB will be freed (install 0 B, remove 3 MiB).
Is this ok [y/N]: y
Running transaction
[1/3] Prepare transaction                                100% |  12.0   B/s |   2.0   B |  00m00s
[2/3] Removing htop-0:3.4.1-3.fc44.x86_64                100% | 933.0   B/s |  14.0   B |  00m00s
[3/3] Removing hwloc-libs-0:2.12.0-3.fc44.x86_64         100% | 136.0   B/s |  32.0   B |  00m00s
Complete!
```

# 2 Керування сервісами через systemctl
```bash
danylo@fedora:~$ sudo systemctl stop sshd
danylo@fedora:~$ systemctl status sshd
○ sshd.service - OpenSSH server daemon
     Loaded: loaded (/usr/lib/systemd/system/sshd.service; disabled; preset: disabled)
    Drop-In: /usr/lib/systemd/system/service.d
             └─10-timeout-abort.conf
     Active: inactive (dead)
       Docs: man:sshd(8)
             man:sshd_config(5)
danylo@fedora:~$ sudo systemctl start sshd
danylo@fedora:~$ systemctl status sshd
● sshd.service - OpenSSH server daemon
     Loaded: loaded (/usr/lib/systemd/system/sshd.service; disabled; preset: disabled)
    Drop-In: /usr/lib/systemd/system/service.d
             └─10-timeout-abort.conf
     Active: active (running) since Fri 2026-05-22 14:28:01 EEST; 12s ago
 Invocation: 0a93859f428b40d0abcc99d1ab78ef82
       Docs: man:sshd(8)
             man:sshd_config(5)
   Main PID: 56345 (sshd)
      Tasks: 1 (limit: 18610)
     Memory: 1.6M (peak: 2.1M)
        CPU: 8ms
     CGroup: /system.slice/sshd.service
             └─56345 "sshd: /usr/sbin/sshd -D [listener] 0 of 10-100 startups"

May 22 14:28:01 fedora systemd[1]: Starting sshd.service - OpenSSH server daemon...
May 22 14:28:01 fedora sshd[56345]: Server listening on 0.0.0.0 port 22.
May 22 14:28:01 fedora sshd[56345]: Server listening on :: port 22.
May 22 14:28:01 fedora systemd[1]: Started sshd.service - OpenSSH server daemon.
danylo@fedora:~$ sudo systemctl enable sshd
Created symlink '/etc/systemd/system/multi-user.target.wants/sshd.service' → '/usr/lib/systemd/system/sshd.service'.
danylo@fedora:~$ systemctl is-enabled sshd
enabled
```
# 3 Робота з логами 
```bash
danylo@fedora:~$ cd /var/log
danylo@fedora:/var/log$ sudo tail -n 10 messages
Mar 22 09:48:02 fedora systemd[6724]: Listening on dbus.socket - D-Bus User Message Bus Socket.
Mar 22 09:48:02 fedora systemd[6724]: Reached target sockets.target - Sockets.
Mar 22 09:48:02 fedora systemd[6724]: Finished systemd-tmpfiles-setup.service - Create User Files and Directories.
Mar 22 09:48:02 fedora systemd[6724]: Reached target basic.target - Basic System.
Mar 22 09:48:02 fedora systemd[6724]: Reached target default.target - Main User Target.
Mar 22 09:48:02 fedora systemd[6724]: Startup finished in 129ms.
Mar 22 09:48:02 fedora systemd[1]: Started user@0.service - User Manager for UID 0.
Mar 22 09:48:02 fedora audit[1]: SERVICE_START pid=1 uid=0 auid=4294967295 ses=4294967295 subj=system_u:system_r:init_t:s0 msg='unit=user@0 comm="systemd" exe="/usr/lib/systemd/systemd" hostname=? addr=? terminal=? res=success'
Mar 22 09:48:02 fedora systemd[1]: Started session-c2.scope - Session c2 of User root.
Mar 22 09:48:02 fedora audit[6707]: AUDIT1105 pid=6707 uid=1000 auid=1000 ses=3 subj=unconfined_u:unconfined_r:unconfined_t:s0-s0:c0.c1023 msg='op=PAM:session_open grantors=pam_keyinit,pam_limits,pam_keyinit,pam_limits,pam_systemd,pam_unix acct="root" exe="/usr/bin/sudo" hostname=fedora addr=? terminal=/dev/pts/0 res=success'
danylo@fedora:/var/log$ journalctl -p err -n 5
May 22 14:19:34 fedora (systemd-stdio-bridge)[54324]: PAM adding faulty module: /usr/lib64/secur>
May 22 14:19:36 fedora (systemd-stdio-bridge)[54387]: PAM unable to dlopen(/usr/lib64/security/p>
May 22 14:19:36 fedora (systemd-stdio-bridge)[54387]: PAM adding faulty module: /usr/lib64/secur>
May 22 14:19:36 fedora (systemd-stdio-bridge)[54455]: PAM unable to dlopen(/usr/lib64/security/p>
May 22 14:19:36 fedora (systemd-stdio-bridge)[54455]: PAM adding faulty module: /usr/lib64/secur>
lines 1-5/5 (END)
danylo@fedora:/var/log$ journalctl -u sshd --since "today"
May 22 14:28:01 fedora systemd[1]: Starting sshd.service - OpenSSH server daemon...
May 22 14:28:01 fedora sshd[56345]: Server listening on 0.0.0.0 port 22.
May 22 14:28:01 fedora sshd[56345]: Server listening on :: port 22.
May 22 14:28:01 fedora systemd[1]: Started sshd.service - OpenSSH server daemon.
```

# 4 Створення власного сервісу 
```sh
#!/bin/bash

while true
do
  date >> /home/$USER/dates.log
  sleep 1
done
```
```service
[Unit]
Description=My Date Logger Script
After=network.target

[Service]
ExecStart=/home/danylo/myscript.sh
Restart=always
User=danylo

[Install]
WantedBy=multi-user.target
```
```bash
danylo@fedora:~$ vim myscript.sh
danylo@fedora:~$ chmod +x ~/myscript.sh
danylo@fedora:~$ sudo vim /etc/systemd/system/myscript.service
danylo@fedora:~$ sudo systemctl daemon-reload
danylo@fedora:~$ sudo systemctl start myscript
danylo@fedora:~$ sudo systemctl enable myscript
danylo@fedora:~$ systemctl status myscript
● myscript.service - My Date Logger Script
     Loaded: loaded (/etc/systemd/system/myscript.service; enabled; preset: disabled)
    Drop-In: /usr/lib/systemd/system/service.d
             └─10-timeout-abort.conf
     Active: active (running) since Fri 2026-05-22 14:44:57 EEST; 8s ago
 Invocation: c301fccf6b5d45c999d97576897479b5
   Main PID: 59496 (bash)
      Tasks: 2 (limit: 18610)
     Memory: 736K (peak: 1.7M)
        CPU: 18ms
     CGroup: /system.slice/myscript.service
             ├─59496 /bin/bash /home/danylo/myscript.sh
             └─59533 sleep 1
danylo@fedora:~$ tail -f ~/dates.log
Fri 22 May 2026 02:45:31 PM EEST
Fri 22 May 2026 02:45:32 PM EEST
Fri 22 May 2026 02:45:33 PM EEST
Fri 22 May 2026 02:45:34 PM EEST
Fri 22 May 2026 02:45:35 PM EEST
Fri 22 May 2026 02:45:36 PM EEST
Fri 22 May 2026 02:45:37 PM EEST
Fri 22 May 2026 02:45:38 PM EEST
Fri 22 May 2026 02:45:39 PM EEST
Fri 22 May 2026 02:45:40 PM EEST
Fri 22 May 2026 02:45:41 PM EEST
Fri 22 May 2026 02:45:42 PM EEST
Fri 22 May 2026 02:45:43 PM EEST
```







