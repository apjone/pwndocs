title: Listeners

# Listeners

## Netcat

Netcat / nc is great little utility. 

```
nc -lvnp {PORT}
```
* -l = Listen
* -v = Verbose Output 
* -n = Do not do any DNS look resolution 
* -p = Port Number ( Under 1024 will require root/sudo )

## Metasploit

Metasploit is a great framework & `meterpreter` is great shell with allot of functionality. 

To use Metasploit to listen for incoming shells we first need to run Metasploit

```
$ msfconsole
```

Once running you will need to choose `multi/handler` as the exploit to use

```
use exploit/multi/handler
```

By default the handler will use `generic/shell_reverse_tcp` as the payload, for `meterpreter` you will need to specify the correct payload depending on OS and `meterpreter` architecture deployed to the target.

* linux 32bit
```
set payload linux/x86/meterpreter/reverse_tcp
```
* linux 64bit
```
set payload linux/x64/meterpreter/reverse_tcp
```
* windows 32bit
```
* set payload windows/meterpreter/reverse_tcp
```
* windows 64bit
```
set windows/x64/meterpreter/reverse_tcp
```

**Required Options**

By default the handler will listen on port `4444` and your LAN IP Address. Normally leaving the port at `4444` is OK, if you do need to change it then you will need to use

```
set LPORT {PORT}
```

When using against targets on the local network the default `LHOST` value should be ok, however if using a VPN to connect to a platform like ***TryHackMe*** or ***HackTheBox*** then we will usually need to listen on the IP of the VPN connection. 

* To get your VPN address use the `ip` command with the device of your VPN ( usualy tun0 )

```
ip address show tun0
```

This will output the details of you VPN connection, you need to look for the `inet ` line which will show the IPv4 address of the device. 

```
4: tun0: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UNKNOWN group default qlen 100
    link/none 
    inet 10.x.x.x/16 brd 10.9.255.255 scope global tun0
       valid_lft forever preferred_lft forever
```

We can then set the `LHOST` option using 

```
set LHOST {IP-ADDRESS}
```

As a quick hack you can use the below command to output the `set` command with the correct VPN address

```
ip address show tun0 | grep -w inet | awk '{printf "set LHOST " $2}' | cut -f1 -d'/'
```
