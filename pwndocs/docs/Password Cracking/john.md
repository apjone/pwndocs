title: John The Ripper

`john` is the first program that pops into the mind when looking at cracking passwords.

# Basic Usage
```
john hashfile --wordlist=/path/to/word/list.txt
```

* Specify Format
```
john hashfile --wordlist=/path/to/word/list.txt --format=HASHTYPE
```

# ssh2john
`ssh2john` *(requires python2)* is python script included within the `john` package to extract the passphrase hash from an encrypted private key into a hash format john can understand.

```
python2 /path/to/ssh2john.py private_key > hash-out
```
Then run `john` against the `hash-out` file.

# zip2john 
`zip2john` is a python script to extract that the password hash from a zip file into a format `john` can understand.

```
/path/to/zip2john out.zip > hash-out
```

Then run `john` against the `hash-out` file.

# *2John

The 2 above are the most common in CTF's but `john` also includes the following scripts.

```
1password2john.py      axcrypt2john.py     diskcryptor2john.py  hccapx2john.py       krb2john.py          mozilla2john.py           pgpdisk2john.py   sspr2john.py
adxcsouf2john.py       bestcrypt2john.py   dmg2john.py          htdigest2john.py     kwallet2john.py      multibit2john.py          pgpsda2john.py    staroffice2john.py
aem2john.py            bitcoin2john.py     DPAPImk2john.py      ibmiscanner2john.py  lastpass2john.py     neo2john.py               pgpwde2john.py    strip2john.py
aix2john.py            bitshares2john.py   ecryptfs2john.py     ikescan2john.py      libreoffice2john.py  netscreen.py              prosody2john.py   telegram2john.py
andotp2john.py         bitwarden2john.py   ejabberd2john.py     iwork2john.py        lotus2john.py        office2john.py            pse2john.py       tezos2john.py
androidbackup2john.py  bks2john.py         electrum2john.py     kdcdump2john.py      luks2john.py         openbsd_softraid2john.py  ps_token2john.py  truecrypt2john.py
androidfde2john.py     blockchain2john.py  encfs2john.py        keychain2john.py     mac2john-alt.py      openssl2john.py           pwsafe2john.py    vmx2john.py
ansible2john.py        ccache2john.py      enpass2john.py       keyring2john.py      mac2john.py          padlock2john.py           radius2john.py
apex2john.py           cracf2john.py       ethereum2john.py     keystore2john.py     mcafee_epo2john.py   pcap2john.py              signal2john.py
applenotes2john.py     dashlane2john.py    filezilla2john.py    kirbi2john.py        monero2john.py       pem2john.py               sipdump2john.py
aruba2john.py          deepsound2john.py   geli2john.py         known_hosts2john.py  money2john.py        pfx2john.py               ssh2john.py
```

# Formats

```
descrypt, bsdicrypt, md5crypt, md5crypt-long, bcrypt, scrypt, LM, AFS, 
tripcode, AndroidBackup, adxcrypt, agilekeychain, aix-ssha1, aix-ssha256, 
aix-ssha512, andOTP, ansible, argon2, as400-des, as400-ssha1, asa-md5, 
AxCrypt, AzureAD, BestCrypt, bfegg, Bitcoin, BitLocker, bitshares, Bitwarden, 
BKS, Blackberry-ES10, WoWSRP, Blockchain, chap, Clipperz, cloudkeychain, 
dynamic_n, cq, CRC32, sha1crypt, sha256crypt, sha512crypt, Citrix_NS10, 
dahua, dashlane, diskcryptor, Django, django-scrypt, dmd5, dmg, dominosec, 
dominosec8, DPAPImk, dragonfly3-32, dragonfly3-64, dragonfly4-32, 
dragonfly4-64, Drupal7, eCryptfs, eigrp, electrum, EncFS, enpass, EPI, 
EPiServer, ethereum, fde, Fortigate256, Fortigate, FormSpring, FVDE, geli, 
gost, gpg, HAVAL-128-4, HAVAL-256-3, hdaa, hMailServer, hsrp, IKE, ipb2, 
itunes-backup, iwork, KeePass, keychain, keyring, keystore, known_hosts, 
krb4, krb5, krb5asrep, krb5pa-sha1, krb5tgs, krb5-17, krb5-18, krb5-3, 
kwallet, lp, lpcli, leet, lotus5, lotus85, LUKS, MD2, mdc2, MediaWiki, 
monero, money, MongoDB, scram, Mozilla, mscash, mscash2, MSCHAPv2, 
mschapv2-naive, krb5pa-md5, mssql, mssql05, mssql12, multibit, mysqlna, 
mysql-sha1, mysql, net-ah, nethalflm, netlm, netlmv2, net-md5, netntlmv2, 
netntlm, netntlm-naive, net-sha1, nk, notes, md5ns, nsec3, NT, o10glogon, 
o3logon, o5logon, ODF, Office, oldoffice, OpenBSD-SoftRAID, openssl-enc, 
oracle, oracle11, Oracle12C, osc, ospf, Padlock, Palshop, Panama, 
PBKDF2-HMAC-MD4, PBKDF2-HMAC-MD5, PBKDF2-HMAC-SHA1, PBKDF2-HMAC-SHA256, 
PBKDF2-HMAC-SHA512, PDF, PEM, pfx, pgpdisk, pgpsda, pgpwde, phpass, PHPS, 
PHPS2, pix-md5, PKZIP, po, postgres, PST, PuTTY, pwsafe, qnx, RACF, 
RACF-KDFAES, radius, RAdmin, RAKP, rar, RAR5, Raw-SHA512, Raw-Blake2, 
Raw-Keccak, Raw-Keccak-256, Raw-MD4, Raw-MD5, Raw-MD5u, Raw-SHA1, 
Raw-SHA1-AxCrypt, Raw-SHA1-Linkedin, Raw-SHA224, Raw-SHA256, Raw-SHA3, 
Raw-SHA384, ripemd-128, ripemd-160, rsvp, Siemens-S7, Salted-SHA1, SSHA512, 
sapb, sapg, saph, sappse, securezip, 7z, Signal, SIP, skein-256, skein-512, 
skey, SL3, Snefru-128, Snefru-256, LastPass, SNMP, solarwinds, SSH, sspr, 
Stribog-256, Stribog-512, STRIP, SunMD5, SybaseASE, Sybase-PROP, tacacs-plus, 
tcp-md5, telegram, tezos, Tiger, tc_aes_xts, tc_ripemd160, tc_ripemd160boot, 
tc_sha512, tc_whirlpool, vdi, OpenVMS, vmx, VNC, vtp, wbb3, whirlpool, 
whirlpool0, whirlpool1, wpapsk, wpapsk-pmk, xmpp-scram, xsha, xsha512, ZIP, 
ZipMonster, plaintext, has-160, HMAC-MD5, HMAC-SHA1, HMAC-SHA224, 
HMAC-SHA256, HMAC-SHA384, HMAC-SHA512, dummy, crypt
```

# Git Install
Sometimes the version of `john` installed as part of teh Operating System may be broked or not be compiled with all the required options. We can install `john` from Github to work around this

```
git clone https://github.com/openwall/john.git
cd john/src  
./configure 
make && sudo make install
```

This will build `john` under `john/run/` where you can run binary or python scripts from without impacting the version already installed.