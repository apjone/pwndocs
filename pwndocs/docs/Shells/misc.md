title: Misc Shell Info

# Stability via Python  

**Python3**
```
python3 -c 'import pty;pty("/bin/bash)'
export TERM=xterm
[ctrl+z]
stty raw -echo; fg
```

**Python2**
```
python -c 'import pty;pty("/bin/bash)'
export TERM=xterm
[ctrl+z]
stty raw -echo; fg
```

# SSH Keys

SSH Keys are used to `ssh servers` instead of passwords. They can also be used as a persistence method.

**Key Generation**

Key pairs are generated by using the `ssh-keygen` command. I recommend generating a specific key pair for CTF's instead of using your usual key pair. 

```
$ ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/home/user/.ssh/id_rsa): id_ctf
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in id_ctf
Your public key has been saved in id_ctf.pub
The key fingerprint is:
SHA256:axD9VTczMb4ej/MYNaXe456hucpo/W7x0u5UA8Nd76I user@host
The key's randomart image is:
+---[RSA 3072]----+
|              .*+|
|       .    .+o.B|
|      .  .   =+o5|
|       . . o Bo+o|
|      . S . + +=+|
|       . Q ....==|
|        = + E+=..|
|       o   .o.4= |
|           oo++ .|
+----[SHA256]-----+
```

This will generate 2 files

* id_ctf = This is the ***private*** key and should not be shared. 

* id_ctf.pub = This is the ***public*** key, this is what should be added to the targets `.ssh/authorized_keys`

As the private key is meant to be private most `ssh` clients will check the permissions to ensure that the key is secure. The file should only be accessible by the user, usual 0600 in octal format.  If required you can run the following command to fix permissions..

```
chmod 0600 id_ctf
```

**Using Keys**

`ssh` clients will usually by default use the `id_rsa` key file in the users home directory. If you want to use a different key then you need to pass the `-i` flag.

```
ssh -i id_ctf user@target
```