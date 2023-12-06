# Ubuntu linux server hardening and security
**Checking latest patches on vulnerability and bugfixes**
```
apt-get -s dist-upgrade
apt-get -s dist-upgrade | grep "^Inst"
```
```
apt-get -s dist-upgrade | grep "^Inst" | grep -i secur
apt-get -s dist-upgrade | grep "^Inst" | awk -F " " '{ print $2 }'
apt-get -s dist-upgrade | grep "^Inst" | awk -F " " '{ print $2 }' | xargs apt-get install
```
