# Ubuntu linux server hardening and security
**Checking latest patches on vulnerability and bugfixes**
```
apt-get -s dist-upgrade
apt-get -s dist-upgrade | grep "^Inst"
```
**Check for securtiy updates**
```
apt-get -s dist-upgrade | grep "^Inst" | grep -i secur
apt-get -s dist-upgrade | grep "^Inst" | awk -F " " '{ print $2 }'
apt-get -s dist-upgrade | grep "^Inst" | awk -F " " '{ print $2 }' | xargs apt-get install
```
# Validation packages
```
apt-cache search debsums
apt-get install debsums -y
debsums -l
debsums -c
```
# Lesson 2 Filesystem protection

```
cat /proc/partitions
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
