# linux-security-hardening

# Ubuntu hardening
```
sudo su
git clone https://github.com/konstruktoid/hardening.git
cd hardening
```
```
nano ubuntu.cfg

change network FW_ADMIN='127.0.0.1' // (1) to 192.168.0.0/24 
CHANGEME='' // (14) to OK
```
```
sudo bash ./ubuntu.sh
```
# Running the test 
```
sudo apt install bats
cd tests
bats *.bats
```
# Runnig test of OPENSCAP REPORT
```
cd /hardening/misc
sudo bash ./genOSCAPreport.sh
```
# Getting hardening Index of the system (lynis score)
```
cd /home
git clone https://github.com/CISOfy/lynis.git
cd lynis
./lynis audit system
```
