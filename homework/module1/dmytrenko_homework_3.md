# 1
```bash
danylo@fedora:~$ ps aux | (head && tail)
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.3  0.1  40136 21760 ?        Ss   16:20   0:01 /usr/lib/systemd/systemd --switched-root --system --deserialize=60 rhgb
root           2  0.0  0.0      0     0 ?        S    16:20   0:00 [kthreadd]
root           3  0.0  0.0      0     0 ?        S    16:20   0:00 [pool_workqueue_release]
root           4  0.0  0.0      0     0 ?        I<   16:20   0:00 [kworker/R-rcu_gp]
root           5  0.0  0.0      0     0 ?        I<   16:20   0:00 [kworker/R-sync_wq]
root           6  0.0  0.0      0     0 ?        I<   16:20   0:00 [kworker/R-kvfree_rcu_reclaim]
root           7  0.0  0.0      0     0 ?        I<   16:20   0:00 [kworker/R-slub_flushwq]
root           8  0.0  0.0      0     0 ?        I<   16:20   0:00 [kworker/R-netns]
root          10  0.0  0.0      0     0 ?        I<   16:20   0:00 [kworker/0:0H-events_highpri]
root        7289  0.0  0.0  17076  7300 ?        S    16:25   0:00 systemd-userwork: waiting...
root        7291  0.0  0.0      0     0 ?        I    16:25   0:00 [kworker/8:0-events_freezable]
danylo      7301  0.0  0.5 1460404316 85976 ?    Sl   16:25   0:00 /usr/lib64/chromium-browser/chromium-browser --type=renderer --crashpad-handler-pid=5356 --enable-crash-reporter=,Built from source for Fedora release 43 (Forty Three) --change-stack-guard-on-fork=enable --ozone-platform=wayland --lang=en-GB --num-raster-threads=4 --enable-main-frame-before-activation --renderer-client-id=23 --time-ticks-at-unix-epoch=-1777728004079611 --launch-time-ticks=344580036 --shared-files=v8_context_snapshot_data:100 --metrics-shmem-handle=4,i,13776388021699521646,16412111984073169713,2097152 --field-trial-handle=3,i,9742307605005861278,14258559308979398286,262144 --enable-features=AcceleratedVideoDecodeLinuxGL,AcceleratedVideoDecodeLinuxZeroCopyGL,AcceleratedVideoEncoder,AllowQt,WaylandLinuxDrmSyncobj,WaylandPerSurfaceScale,WaylandUiScale --disable-features=EyeDropper,LensOverlay --variations-seed-version --pseudonymization-salt-handle=7,i,1398081988294936552,13260638892881295743,4 --trace-process-track-uuid=3190709007863834021
root        7310  0.0  0.0      0     0 ?        I<   16:25   0:00 [kworker/u65:2]
root        7339  0.0  0.0  17076  7244 ?        S    16:25   0:00 systemd-userwork: waiting...
root        7340  0.0  0.0      0     0 ?        I    16:25   0:00 [kworker/6:1-mm_percpu_wq]
root        7362  0.0  0.0      0     0 ?        I    16:26   0:00 [kworker/12:0]
danylo      7377  0.0  0.0 234652  4784 pts/1    R+   16:27   0:00 ps aux
danylo      7378  0.0  0.0 233416  3412 pts/1    S+   16:27   0:00 /usr/bin/bash
danylo      7379  0.0  0.0 230368  2124 pts/1    S+   16:27   0:00 head
danylo@fedora:~$ top
top - 16:33:12 up 13 min,  2 users,  load average: 0.17, 0.19, 0.17
Tasks: 417 total,   1 running, 416 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.9 us,  0.5 sy,  0.0 ni, 98.2 id,  0.0 wa,  0.2 hi,  0.1 si,  0.0 st 
MiB Mem :  15681.0 total,   8895.4 free,   4119.0 used,   3709.5 buff/cache     
MiB Swap:   8192.0 total,   8192.0 free,      0.0 used.  11562.0 avail Mem 

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND                      
   6892 danylo    20   0 1392.9g 445256 154088 S   7.6   2.8   0:29.44 chromium-browse              
   5344 danylo    20   0   49.6g 412212 261396 S   0.3   2.6   0:22.57 chromium-browse              
   3850 danylo    20   0 3584236 370884 193520 S   0.0   2.3   0:20.28 gnome-software               
   3465 danylo    20   0   10.1g 337416 161336 S   8.6   2.1   0:38.96 gnome-shell                  
   5467 danylo    20   0   49.6g 256092 140660 S   1.7   1.6   0:27.97 chromium-browse              
   5539 danylo    20   0 1394.8g 246116 140060 S   0.0   1.5   0:08.34 chromium-browse              
   6945 danylo    20   0 2587400 232824 139012 S   5.3   1.4   0:06.46 ptyxis                       
   5613 danylo    20   0 1392.9g 221888 134436 S   0.0   1.4   0:04.94 chromium-browse              
   5618 danylo    20   0 1392.9g 204744 126108 S   0.0   1.3   0:02.08 chromium-browse              
   6804 danylo    20   0 1392.9g 174356 136220 S   0.0   1.1   0:00.81 chromium-browse              
   5737 danylo    20   0 1392.9g 148376 114232 S   0.0   0.9   0:00.14 chromium-browse              
   4721 danylo    20   0 1173664 126416  91852 S   0.0   0.8   0:00.38 mutter-x11-fram              
   7468 root      20   0  726292 123296  25780 S   0.0   0.8   0:00.70 packagekitd                  
   5469 danylo    20   0   48.9g 117628  85828 S   0.0   0.7   0:02.76 chromium-browse              
   5796 danylo    20   0  618408 106200  44828 S   0.0   0.7   0:00.52 ibus-engine-tb               
   4708 danylo    20   0  521556 105180  76064 S   0.0   0.7   0:00.16 Xwayland                     
   5502 danylo    20   0 1394.6g 102212  74464 S   0.0   0.6   0:00.06 chromium-browse              
   7301 danylo    20   0 1392.8g  85976  60816 S   0.0   0.5   0:00.01 chromium-browse              
   5019 danylo    20   0 1505568  77256  54360 S   0.0   0.5   0:00.38 gnome-calendar               
   3846 danylo    20   0 1286260  73372  55936 S   0.0   0.5   0:00.15 evolution-alarm              
   5363 danylo    20   0   49.1g  72652  52700 S   0.0   0.5   0:00.06 chromium-browse  
```
- найбільше спошиває chrome, але він розбитий на багато процесів
- bash має PID 7168

# 2
```bash
danylo@fedora:~$ sleep 1000 &
[1] 7586
danylo@fedora:~$ jobs
[1]+  Running                    sleep 1000 &
danylo@fedora:~$ fg %1
sleep 1000
^Z
[1]+  Stopped                    sleep 1000
danylo@fedora:~$ ps aux | grep sleep
danylo      7586  0.0  0.0 230352  2300 pts/1    T    16:37   0:00 sleep 1000
danylo      7607  0.0  0.0 231268  2552 pts/1    S+   16:38   0:00 grep --color=auto sleep
danylo@fedora:~$ kill -9 7586
[1]+  Killed                     sleep 1000
danylo@fedora:~$ nohup sleep 1000 &
```

# 3
```bash
danylo@fedora:~$ nice -n 10 sleep 1000 &
[1] 7632
danylo@fedora:~$ renice 15 -p 7632
7632 (process ID) old priority 10, new priority 15
danylo@fedora:~$ ulimit -a
real-time non-blocking time  (microseconds, -R) unlimited
core file size              (blocks, -c) unlimited
data seg size               (kbytes, -d) unlimited
scheduling priority                 (-e) 0
file size                   (blocks, -f) unlimited
pending signals                     (-i) 62060
max locked memory           (kbytes, -l) 8192
max memory size             (kbytes, -m) unlimited
open files                          (-n) 1024
pipe size                (512 bytes, -p) 8
POSIX message queues         (bytes, -q) 819200
real-time priority                  (-r) 0
stack size                  (kbytes, -s) 8192
cpu time                   (seconds, -t) unlimited
max user processes                  (-u) 62060
virtual memory              (kbytes, -v) unlimited
file locks                          (-x) unlimited
```

# 4
```bash
danylo@fedora:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/nvme0n1p6  219G   76G  141G  35% /
devtmpfs        7.6G     0  7.6G   0% /dev
tmpfs           7.7G   54M  7.7G   1% /dev/shm
efivarfs        192K  117K   71K  63% /sys/firmware/efi/efivars
tmpfs           3.1G  2.4M  3.1G   1% /run
tmpfs           1.0M     0  1.0M   0% /run/credentials/systemd-journald.service
tmpfs           7.7G   14M  7.7G   1% /tmp
/dev/nvme0n1p6  219G   76G  141G  35% /home
/dev/nvme0n1p5  2.0G  651M  1.2G  36% /boot
/dev/nvme0n1p1   96M   52M   45M  54% /boot/efi
tmpfs           1.0M     0  1.0M   0% /run/credentials/systemd-resolved.service
tmpfs           1.6G  168K  1.6G   1% /run/user/1000
danylo@fedora:~$ free -h
               total        used        free      shared  buff/cache   available
Mem:            15Gi       3.8Gi       8.9Gi       722Mi       3.6Gi        11Gi
Swap:          8.0Gi          0B       8.0Gi
```
