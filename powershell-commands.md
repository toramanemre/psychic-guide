## portscan with 3 second timeout 

```
1..65535 | % { $client = New-Object Net.Sockets.TcpClient; $asyncResult = $client.BeginConnect("portquiz.net", $_, $null, $null); if ($asyncResult.AsyncWaitHandle.WaitOne(3000, $true)) { $client.EndConnect($asyncResult); if ($client.Connected) { "Port $_ is open!" } else { "Port $_ is closed." } } else { "Port $_ timed out." }; $client.Close() } 2>$null
```
