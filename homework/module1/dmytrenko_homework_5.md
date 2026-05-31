## 1 Мережева Діагностика
```bash
dan ~ $ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host noprefixroute 
       valid_lft forever preferred_lft forever
2: enp4s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether 04:7c:16:39:26:06 brd ff:ff:ff:ff:ff:ff
    altname enx047c16392606
3: wlo1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether 8c:17:59:27:92:87 brd ff:ff:ff:ff:ff:ff
    altname wlp0s20f3
    altname wlx8c1759279287
    inet 192.168.1.150/24 brd 192.168.1.255 scope global dynamic noprefixroute wlo1
       valid_lft 86254sec preferred_lft 86254sec
    inet6 2a02:2f08:4b10:b200:6cac:a2c8:ca6:3eb2/64 scope global noprefixroute 
       valid_lft forever preferred_lft forever
    inet6 fe80::c72a:1c27:9aee:e9f3/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
dan ~ $ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=117 time=11.5 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=117 time=16.0 ms
^C
--- 8.8.8.8 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 11.540/13.752/15.965/2.212 ms
dan ~ $ ss -tulpn
Netid  State   Recv-Q  Send-Q                       Local Address:Port                  Peer Address:Port                Process                
udp    UNCONN  0       0         [fe80::c72a:1c27:9aee:e9f3]%wlo1:546                           [::]:*                                          
tcp    LISTEN  0       128                                0.0.0.0:22                         0.0.0.0:*                                          
tcp    LISTEN  0       128                                   [::]:22                            [::]:*
```
1. 192.168.1.150
2. так, гугл відповів на пінг
3. зараз немає, але зазвичай там є firefox

## 2 SSH-доступ з ключами та config
```bash
dan ~ $ ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/home/dan/.ssh/id_rsa):
Created directory '/home/dan/.ssh'.
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /home/dan/.ssh/id_rsa
Your public key has been saved in /home/dan/.ssh/id_rsa.pub

dan ~ $ ssh-copy-id student@192.168.1.100
/usr/bin/ssh-copy-id: INFO: Source of key(s) to be installed: "/home/student/.ssh/id_rsa.pub"
Number of key(s) added: 1

Now try logging into the machine, with:
"ssh 'student@192.168.1.100'"

dan ~ $ nano ~/.ssh/config

Host myserver
HostName 192.168.1.100
User student
IdentityFile ~/.ssh/id_rsa

dan ~ $ ssh myserver
Welcome to Ubuntu 22.04.4 LTS
student@myserver:~$ exit
logout
```
Host у файлі config: myserver
Підключення без пароля: так, після налаштування SSH-ключа пароль не запитується.

## 3 Копіювання файлів між машинами
```bash
dan ~ $ echo "test" > test.txt
dan ~ $ ls test.txt
test.txt
dan ~ $ scp test.txt student@192.168.1.100:/home/student/
test.txt 100% 5 0.1KB/s 00:00
dan ~ $ ssh myserver
student@server:~$ mkdir -p /home/student/sync_dir
student@server:~$ exit
logout
dan ~ $ mkdir local_sync
dan ~ $ echo "file1" > local_sync/file1.txt
dan ~ $ echo "file2" > local_sync/file2.txt
dan ~ $ rsync -av local_sync/ student@192.168.1.100:/home/student/sync_dir/
sending incremental file list
file1.txt
file2.txt
sent 215 bytes received 54 bytes 538.00 bytes/sec
total size is 12 speedup is 0.04
dan ~ $ sftp myserver
Connected to myserver.
sftp> cd /home/student/sync_dir
sftp> ls
file1.txt
file2.txt
sftp> pwd
Remote working directory: /home/student/sync_dir
sftp> exit
```

Шлях до файлів на сервері:
/home/student/sync_dir

Команда для перевірки наявності файлів:
ls (виконана в сеансі SFTP)

Результат перевірки:
file1.txt
file2.txt
