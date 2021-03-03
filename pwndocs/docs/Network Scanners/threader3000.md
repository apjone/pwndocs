title: Threader3000

# Install

Threader3000 is a multi-threaded python port scanner than be downloaded via `pip` or from github [https://github.com/dievus/threader3000](https://github.com/dievus/threader3000)

```
pip3 install threader3000
```

# Usage

Threader can be run from the cli and will prompt for the traget

```
------------------------------------------------------------
        Threader 3000 - Multi-threaded Port Scanner          
                       Version 1.0.7                    
                   A project by The Mayor               
------------------------------------------------------------
Enter your target IP address or URL here: 127.0.0.1
------------------------------------------------------------
Scanning target 127.0.0.1
Time started: 2021-03-01 01:49:10.870540
------------------------------------------------------------
Port 22 is open
Port 631 is open
Port 3306 is open
Port 6463 is open
Port 33060 is open
Port 37360 is open
Port 41839 is open
Port 46098 is open
Port scan completed in 0:00:12.827226
------------------------------------------------------------
Threader3000 recommends the following Nmap scan:
************************************************************
nmap -p22,631,3306,6463,33060,37360,41839,46098 -sV -sC -T4 -Pn -oA 127.0.0.1 127.0.0.1
************************************************************
Would you like to run Nmap or quit to terminal?
------------------------------------------------------------
1 = Run suggested Nmap scan
2 = Run another Threader3000 scan
3 = Exit to terminal
------------------------------------------------------------
```

After running you will get the option to run a suggested `nmap` scan