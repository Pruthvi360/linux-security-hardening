# Redhat linux server hardening and security
**Sites for the getting latest updates of vulnerability**
```
https://www.cve.org/news/index.html
https://access.redhat.com/security/security-updates/cve)https://access.redhat.com/security/security-updates/cve
```
# Checking latest patches on vulnerability and bugfixes
```
yum updateinfo
yum updateinfo list
yum updateinfo RHSA-2016:0176 | less
```
# Validating packages
```
rpm -Va
```

# Lesson 2 Filesystem protection

**Mount Encrypted Device**
```
cat /proc/partitions
fdisk /dev/sdb
new
p
1
2048
+512M
w
```
```
crytpsetup luksFormat /dev/sdb1
yes
Enter passphrase: 1996

cryptsetup luksOpen /dev/sdb1 secret
Enter passphrase: 1996
cd /dev/mapper/
\ls


mkfs.ext4 /dev/mapper/secret
mkdir /secret
mount /dev/mapper/secret /secret
mount
```
**Disconnet Encrypted Device**
```
unmount /secret
cryptsetup luksClose /dev/mapper/secret
cd /dev/mapper
\ls    # Should not find any secret directory
```


