title: Rustscan
# Rustscan

*RustScan is a modern take on the port scanner. Sleek & fast. All while providing extensive extendability to you.*

*Not to mention RustScan uses Adaptive Learning to improve itself over time, making it the best port scanner for you.*

# Installation 

Rustscan can be [downloaded from github](https://github.com/RustScan/RustScan/releases/latest) as a `.deb` for installation on debian based systems such as Kali & Ubuntu.

```
sudo dpkg -i Downloads/rustscan_version_amd64.deb
```

# Usage

* Quick Scan
```
rustscan -a {IP-ADDRESS}
```

* Increase ulimit to increase rustscan speed ( note: this can hurt target server )

```
rustscan -a {IP-ADDRESS} --ulimit {limit}
```

* Passing arguments to nmap

```
rustscan -a {IP-ADDRESS} -- {NMAP-ARGUMENTS}
```
*eg*
```
rustscan -a ctfbox --ulimit 10000 -- -sC -sV -oA output -A -v
```