# 🛶 SSH

## SSH Keys

### Structure

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

### Setup (macOS)

Create First Key

```bash
# create key with rsa type, 4096 bits, with email in comment
$ ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

Edit Config

```bash
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
  User corporate
  AddKeysToAgent yes
  IdentityFile ~/.ssh/corporate_key
  UseKeychain yes
  IdentitiesOnly yes
```

Create second key

```bash
$ ssh-keygen -t rsa -b 4096 -C "your_corporate_email@example.com"
# Generating public/private rsa key pair.
# Enter file in which to save the key (/home/username/.ssh/id_rsa):
# add path and name for key^
$ /home/username/.ssh/corporate_key
```

Add passphrases for Keys to KeyChain (flag -K - depricated)

```bash
ssh-add --apple-use-keychain ~/.ssh/id_rsa
ssh-add --apple-use-keychain ~/.ssh/corporate_key
```

Change passphrase (if needed)

```bash
ssh-keygen -p
```

Use chosen key

<pre class="language-bash"><code class="lang-bash"># ssh with identity_file
<strong>ssh -i ~/.ssh/corporate_key root@192.168.1.1
</strong><strong># use default
</strong>ssh root@138.68.92.49</code></pre>

## Copy Public Key

```
$ cat ~/.ssh/id_rsa.pub | pbcopy
```

## SSH Connect

```bash
ssh username@remote_host
# without checking host
ssh -o StrictHostKeyChecking=no username@remote_host 
```

## Links

doc - [https://www.digitalocean.com/community/tutorials/ssh-essentials-working-with-ssh-servers-clients-and-keys#ssh-overview](https://www.digitalocean.com/community/tutorials/ssh-essentials-working-with-ssh-servers-clients-and-keys#ssh-overview)\\
