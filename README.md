# Day 8 – User Groups Management, Permissions
---
### Multiple User Creation and groups (Task 1)
##### 1.Create Groups
```
sudo groupadd developers
sudo groupadd testers
sudo groupadd admins
```

#### 2.Create Users
```
sudo useradd -m -G developers alice
sudo useradd -m -G testers bob
sudo useradd -m -G admins charlie
```

#### 3.Set Passwords for Users
```
sudo passwd alice
sudo passwd bob
sudo passwd charlie
```

#### 4.Create Project Directory & Assign Permissions
```
sudo mkdir /projectX
sudo chown root:developers /projectX
sudo chmod 770 /projectX
```

#### 5. Verify Group Membership
```
id alice
id bob
```
---
### Set password policies(Task 2)
---
#### 1.Set password aging policy
```
Set password aging policy
```
#### 2.Force Password Expiry Immediately
```
sudo passwd --expire bob
```
#### 3.Set Account Expiration Date
```
sudo chage -E 2025-12-31 charlie
```
#### 4.Lock and Unlock a User Account
```
sudo passwd -l alice #Lock
sudo passwd -u alice #Unllock
```
#### 5.Disable Login After Inactivity
```
sudo chage -I 30 bob
```
#### 6.Verifiy Policies
```
sudo chage -l alice
sudo chage -l bob
```
---
### Configure Sudo Privileges (Task 3)
---
#### 1.Open the sudoers File Safely
```
sudo visudo
```
#### 2.Add Rule for User alice
```
alice ALL=(ALL) /bin/systemctl restart ssh, /bin/systemctl status ssh
```
#### 3.Allow bob to Run Only Network Commands
```
bob ALL=(ALL) /usr/sbin/ifconfig, /usr/sbin/ip
```
#### 4.Allow charlie Passwordless Access to Check Disk Space
```
charlie ALL=(ALL) NOPASSWD: /bin/df
```
#### 5.Test the Rules
```
sudo -l -U alice
sudo -l -U bob
sudo -l -U charlie
```
---


  





