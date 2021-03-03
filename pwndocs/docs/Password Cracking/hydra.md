title: Hydra

Unlike `john` or `hashcat` that crack passwords offline `hydra` is an online brute force tool

# Usage
```
Hydra v9.0 (c) 2019 by van Hauser/THC - Please do not use in military or secret service organizations, or for illegal purposes.

Syntax: hydra [[[-l LOGIN|-L FILE] [-p PASS|-P FILE]] | [-C FILE]] [-e nsr] [-o FILE] [-t TASKS] [-M FILE [-T TASKS]] [-w TIME] [-W TIME] [-f] [-s PORT] [-x MIN:MAX:CHARSET] [-c TIME] [-ISOuvVd46] [service://server[:PORT][/OPT]]
```

`hydra` basic usage requires a username, password & target. As you can see from above you can specify files containing usernames and/or passwords. 

* Try to brute force user `bob` over `ssh`
```
hydra -l bob -P /path/to/word/list.txt target ssh
```

* Try to brute force a list of users using `summer2021 `
```
hydra -l users.txt -p summer2021 target ssh
```

* Try to brute force a list of users using a wordlist
```
hydra -L users.txt -P /path/to/word/list.txt target ssh
```

# Wordpress
To brute force `wordpress` with `hydra` we can use the below

```
hydra -l username -P /path/to/word/list.txt host -V http-form-post '/wp-login.php:log=^USER^&pwd=^PASS^&wp-submit=Log In&testcookie=1:S=Location'
```