# 1. Register the System:
Loging with Redhat account:
```
sudo subscription-manager register
```
# 2. Attach a Subscription:
```
sudo subscription-manager attach --pool=<pool-id>
sudo subscription-manager attach --pool=f0193817-f570-415e-95d4-7aa7c6166983
```
# 3. Refresh Repositories:
```
sudo subscription-manager repos --list
```
# 4. Check Subscription Status:
```
sudo subscription-manager status
```
# Check for Updates:
```
sudo dnf update
```
