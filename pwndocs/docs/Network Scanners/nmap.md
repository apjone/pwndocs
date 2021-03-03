title: nmap

`nmap` is the goto cli tool that ships with `kali` and versatile and extendable. 

* Fast scan

```
nmap -F {IP-ADDRESS}
```

* CTF scan

```
nmap -Pn -v -oA output -sC -sV -A {IP-ADDRESS}
```

* Pn - treat all hosts alive, useful when ICMP is blocked
* v - verbose output
* oA - output scan to all formats ( txt, xml & grepable )
* sC - run default nmap scripts
* sV - version detection 
* A - enable OS detection, version detection, script scanning, and traceroute