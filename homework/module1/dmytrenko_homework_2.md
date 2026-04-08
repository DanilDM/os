# 1

```bash
danylo@fedora:~$ cd /
danylo@fedora:/$ ls
afs  boot      dev  home  lib64  mnt  proc  run   srv  tmp  var
bin  builddir  etc  lib   media  opt  root  sbin  sys  usr
danylo@fedora:/$ cd etc/
danylo@fedora:/etc$ ls
abrt                     gdbinit.d                 mime.types           sddm.conf.d
adjtime                  gdm                       mke2fs.conf          security
aliases                  geoclue                   modprobe.d           selinux
alsa                     gimp                      modules-load.d       services
alternatives             glvnd                     motd                 sestatus.conf
anaconda                 gnome-remote-desktop      motd.d               sgml
anthy-unicode.conf       gnupg                     mtab                 shadow
asound.conf              GREP_COLORS               mtools.conf          shadow-
audit                    groff                     my.cnf               shells
authselect               group                     my.cnf.d             skel
avahi                    group-                    nanorc               smartmontools
bash_completion.d        grub2.cfg                 ndctl                sos
bashrc                   grub2-efi.cfg             ndctl.conf.d         speech-dispatcher
bindresvport.blacklist   grub.d                    netconfig            ssh
binfmt.d                 gshadow                   NetworkManager       ssl
bluetooth                gshadow-                  networks             sssd
brlapi.key               gss                       nfs.conf             statetab.d
brltty                   gssproxy                  nfsmount.conf        subgid
brltty.conf              host.conf                 nftables             subgid-
ceph                     hostname                  nilfs_cleanerd.conf  subuid
chromium                 hosts                     nsswitch.conf        subuid-
chrony.conf              hp                        nvidia               sudo.conf
cifs-utils               httpd                     nvme                 sudoers
cockpit                  i3                        openal               sudoers.d
colord                   idmapd.conf               OpenCL               sway
containers               ImageMagick-7             openldap             swid
cpupower-service.conf    initial-setup             opensc.conf          swtpm-localca.conf
credstore                inittab                   opensc-x86_64.conf   swtpm-localca.options
credstore.encrypted      inputrc                   openvpn              swtpm_setup.conf
crypto-policies          ipp-usb                   opt                  sysconfig
crypttab                 iscsi                     os-release           sysctl.conf
csh.cshrc                issue                     ostree               sysctl.d
csh.login                issue.d                   PackageKit           systemd
cups                     issue.net                 pam.d                system-release
cupshelpers              java                      paperspecs           system-release-cpe
dbus-1                   jvm                       passim.conf          terminfo
dconf                    jvm-common                passwd               thermald
debuginfod               kde                       passwd-              tmpfiles.d
default                  kdump                     passwdqc.conf        tpm2-tss
depmod.d                 kdump.conf                pinforc              Trolltech.conf
dhcp                     kernel                    pkcs11               trusted-key.key
DIR_COLORS               keys                      pkgconfig            ts.conf
DIR_COLORS.lightbgcolor  keyutils                  pki                  tuned
dnf                      krb5.conf                 plymouth             udev
dnsmasq.conf             krb5.conf.d               pm                   udisks2
dnsmasq.d                ld.so.cache               polkit-1             ufw
dracut.conf              ld.so.conf                popt.d               unbound
dracut.conf.d            ld.so.conf.d              ppp                  updatedb.conf
eac                      libaudit.conf             printcap             UPower
egl                      libblockdev               profile              uresourced.conf
environment              libibverbs.d              profile.d            usb_modeswitch.conf
ethertypes               libnl                     protocols            userdb
exports                  libreport                 pulse                vconsole.conf
exports.d                libssh                    qemu                 vdpau_wrapper.cfg
favicon.png              libuser.conf              qemu-ga              vimrc
fedora-release           libvirt                   rc.d                 virc
filesystems              lightdm                   reader.conf.d        vmware-tools
firewalld                locale.conf               redhat-release       vpl
flatpak                  localtime                 request-key.conf     vpnc
flexiblasrc              login.defs                request-key.d        vulkan
flexiblasrc.d            logrotate.conf            resolv.conf          whois.conf
fonts                    logrotate.d               rpc                  wireplumber
foomatic                 lvm                       rpm                  wpa_supplicant
fprintd.conf             machine-id                rpmdevtools          X11
fstab                    magic                     rsyncd.conf          xattr.conf
fstab.script             mailcap                   rwtab.d              xdg
fuse.conf                makedumpfile.conf.sample  rygel.conf           xml
fwupd                    man_db.conf               samba                yum.repos.d
gcrypt                   mcelog                    sane.d
gdbinit                  mdevctl.d                 sasl2
danylo@fedora:/etc$ cd /home
danylo@fedora:/home$ ls
danylo
```

# 2

```bash
danylo@fedora:~$ mkdir ~/lab2
danylo@fedora:~$ touch ~/lab2/file.txt
danylo@fedora:~$ cp ~/lab2/file.txt ~/lab2/file_copy.txt
danylo@fedora:~$ mv ~/lab2/file_copy.txt ~/lab2/file_renamed.txt
danylo@fedora:~$ ln ~/lab2/file.txt ~/lab2/file_hardlink.txt
danylo@fedora:~$ ln -s ~/lab2/file.txt ~/lab2/file_symlink.txt
danylo@fedora:~$ find ~/lab2 -name "file.txt"
/home/danylo/lab2/file.txt
danylo@fedora:~$ ls -la ~/lab2
total 4
drwxr-xr-x. 1 danylo danylo 114 Apr  8 12:11 .
drwx------. 1 danylo danylo 604 Apr  8 12:10 ..
-rw-r--r--. 2 danylo danylo   0 Apr  8 12:10 file_hardlink.txt
-rw-r--r--. 1 danylo danylo   0 Apr  8 12:10 file_renamed.txt
lrwxrwxrwx. 1 danylo danylo  26 Apr  8 12:11 file_symlink.txt -> /home/danylo/lab2/file.txt
-rw-r--r--. 2 danylo danylo   0 Apr  8 12:10 file.txt
```

# 3

```bash
danylo@fedora:~$ ls -l ~/lab2/file.txt
-rw-r--r--. 2 danylo danylo 0 Apr  8 12:10 /home/danylo/lab2/file.txt
danylo@fedora:~$ chmod 444 ~/lab2/file.txt
danylo@fedora:~$ chmod u+w ~/lab2/file.txt
danylo@fedora:~$ umask
0022
danylo@fedora:~$ umask 022
```

# 4

```bash
danylo@fedora:~$ sudo useradd -m -s /bin/bash trainee
[sudo] password for danylo:
danylo@fedora:~$ sudo usermod -aG wheel trainee
danylo@fedora:~$ grep trainee /etc/passwd
trainee:x:1001:1001::/home/trainee:/bin/bash
```
