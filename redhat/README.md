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
**Using security related mount options**
```
man mount

/tmp, /var, /var/lag, /usr, /home

nodev              ---> No device can be accessed if directory is attached to this. can be added to all dicrectory above except /home
nosuid             ---> files will not be executed by the permission of the person who execute it but it will executed by permission of the owner of the Dir or file. It should not be applied to /home dir
noexec             ---> Prevents user run executeable on that directory.
```
**Mounting Directory to noexec or nosuid or nodev**
```
mount -o remount,noexec /dev/mapper/secret
mount #Check the mount option on that directory
```
# File System Table (fstab) Configuration

The `fstab` file is a crucial configuration file in Unix-like operating systems, including Linux. It defines how file systems are mounted during the boot process.

## fstab Entry

Here's a breakdown of a typical `fstab` entry:

```plaintext
UUID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx   /mnt/data   ext4   defaults   0   2



Certainly! If you want to include information about fstab in a README.md file on GitHub, you can format it for better readability. Here's an example:

markdown
Copy code
# File System Table (fstab) Configuration

The `fstab` file is a crucial configuration file in Unix-like operating systems, including Linux. It defines how file systems are mounted during the boot process.

## Sample fstab Entry

Here's a breakdown of a typical `fstab` entry:
Check with `blkid` for existing mount directory of `fstab`:

```plaintext
UUID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx   /mnt/data   ext4   defaults   0   2
```
```
UUID (Universally Unique Identifier): A unique identifier for the file system.
Mount Point: The directory where the file system is mounted.
File System Type: The type of file system on the partition (e.g., ext4, ntfs, xfs).
Mount Options: Additional options for mounting the file system (e.g., rw for read and write access).
Dump Flag: Used by the dump command (0 means no dump).
File System Check Order: Used by the fsck command (0 means no check during boot).
```
