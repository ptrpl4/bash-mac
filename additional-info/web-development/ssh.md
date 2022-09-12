# SSH

## SSH Keys

Structure

/Users/current\_user/.ssh

```
.
├── one_more_key
├── one_more_key.pub
├── config
├── id_rsa
├── id_rsa.pub
└── known_hosts
```

Setup (macOS)

Create First Key

```
$ ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
# Generating public/private rsa key pair.
# Enter file in which to save the key (/home/username/.ssh/id_rsa):
# Press Enter^
$ Enter passphrase (empty for no passphrase):
# then add passphrase
```

Edit Config

```
$ nano ~/.ssh/config
```

```
Host github
  HostName github.com
  User main
  AddKeysToAgent yes
  IdentityFile ~/.ssh/id_rsa
  UseKeychain yes
  IdentitiesOnly yes
  
Host bitbucket-corporate
  HostName bitbucket.org
  User second
  AddKeysToAgent yes
  IdentityFile ~/.ssh/second
  UseKeychain yes
  IdentitiesOnly yes
```

Create second key

```
$ ssh-keygen
# Generating public/private rsa key pair.
# Enter file in which to save the key (/home/username/.ssh/id_rsa):
# add path and name for key^
$ /home/username/.ssh/second
```

Add passphrases for Keys to KeyChain (flag -K - depricated)

```bash
$ ssh-add --apple-use-keychain ~/.ssh/id_rsa
$ ssh-add --apple-use-keychain ~/.ssh/second
```

Change passphrase

```bash
$ ssh-keygen -p
```

## Copy Public Key

```
$ cat ~/.ssh/id_rsa.pub | pbcopy
```

## SSH Connect

```bash
$ ssh username@remote_host
```

## Links

doc - [https://www.digitalocean.com/community/tutorials/ssh-essentials-working-with-ssh-servers-clients-and-keys#ssh-overview](https://www.digitalocean.com/community/tutorials/ssh-essentials-working-with-ssh-servers-clients-and-keys#ssh-overview)\\
