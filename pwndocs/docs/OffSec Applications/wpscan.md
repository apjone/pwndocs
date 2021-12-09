title: WPScan

# WPScan

`WPScan` is a ruby script for probing wordpress sites for vulnerabilities and out of data software.

## Installation

`WPScan` is installed by default on Kali, for other distributions you can install via ruby package manager `gem`.

```
sudo gem install wpscan
```

## Usage

* Basic usage
```
wpscan --url http://wordpress.site
```

* Enumerating Users
```
wpscan --url http://wordpress.site -e u
```

* Brute forcing users
```
wpscan --url http://flooritphotography.com -P /path/to/word/list.txt -U users.txt
```
* You can also choose an attack method by using the below options

```
--password-attack ATTACK                  Force the supplied attack to be used rather than automatically determining one.

Available choices: wp-login, xmlrpc, xmlrpc-multicall
```