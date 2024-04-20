# 🛶 SSH

links

- https://www.digitalocean.com/community/tutorials/ssh-essentials-working-with-ssh-servers-clients-and-keys#ssh-overview

## .shh folder

### Structure

```bash
tree /Users/$USER/.ssh
.
├── one_more_key
├── one_more_key.pub
├── config
├── id_rsa
├── id_rsa.pub
└── known_hosts
```

## Setup Instructions

Create Keys

```bash
cd ~/.ssh

# create key with rsa type, 4096 bits, with email in comment
ssh-keygen -t rsa -b 4096 -C "your_dev_email@example.com"

ssh-keygen -t rsa -b 4096 -C "your_corporate_email@example.com"

# edit config file
nano ~/.ssh/config
```

example config

```bash
cat ~/.ssh/config

Host github
  HostName github.com
  User main
  AddKeysToAgent yes
  IdentityFile ~/.ssh/id_rsa
  UseKeychain yes
  IdentitiesOnly yes
  
Host bitbucket-corporate
  HostName bitbucket.org
  User corporate
  AddKeysToAgent yes
  IdentityFile ~/.ssh/corporate_key
  UseKeychain yes
  IdentitiesOnly yes
```

Add passphrases for Keys to KeyChain (flag -K - depricated)

```bash
ssh-add --apple-use-keychain ~/.ssh/id_rsa
ssh-add --apple-use-keychain ~/.ssh/corporate_key

# change passphrase (if needed)
ssh-keygen -p
```

Use chosen key

```bash
# ssh with identity_file
ssh -i ~/.ssh/corporate_key root@192.168.1.1

# use default key
ssh root@123.32.11.10
```

## Copy Public Key

```bash
$ cat ~/.ssh/id_rsa.pub | pbcopy
```

## SSH Connect

```bash
ssh username@remote_host
# without checking host
ssh -o StrictHostKeyChecking=no username@remote_host 
```
