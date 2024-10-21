## Домашнее задание к занятию «Защита сети» "Воронин Владислав"


### Задание 1

В логе suricata мы видим что идет сканирование нашего хоста с ip 192.168.56.101 на разные службы по соответствующим портам.

```
vodin@ubuntu-VBox:~$ sudo tail -f /var/log/suricata/fast.log
[sudo] пароль для vodin: 
10/21/2024-12:04:27.674312  [**] [1:2010935:3] ET SCAN Suspicious inbound to MSSQL port 1433 [**] [Classification: Potentially Bad Traffic] [Priority: 2] {TCP} 192.168.56.101:48398 -> 192.168.56.110:1433
10/21/2024-12:04:55.315153  [**] [1:2010937:3] ET SCAN Suspicious inbound to mySQL port 3306 [**] [Classification: Potentially Bad Traffic] [Priority: 2] {TCP} 192.168.56.101:50828 -> 192.168.56.110:3306
10/21/2024-12:04:55.317925  [**] [1:2010935:3] ET SCAN Suspicious inbound to MSSQL port 1433 [**] [Classification: Potentially Bad Traffic] [Priority: 2] {TCP} 192.168.56.101:50828 -> 192.168.56.110:1433
10/21/2024-12:04:55.324971  [**] [1:2010939:3] ET SCAN Suspicious inbound to PostgreSQL port 5432 [**] [Classification: Potentially Bad Traffic] [Priority: 2] {TCP} 192.168.56.101:50828 -> 192.168.56.110:5432
10/21/2024-12:04:55.325092  [**] [1:2002911:6] ET SCAN Potential VNC Scan 5900-5920 [**] [Classification: Attempted Information Leak] [Priority: 2] {TCP} 192.168.56.101:50828 -> 192.168.56.110:5903
10/21/2024-12:04:55.331928  [**] [1:2002910:6] ET SCAN Potential VNC Scan 5800-5820 [**] [Classification: Attempted Information Leak] [Priority: 2] {TCP} 192.168.56.101:50828 -> 192.168.56.110:5800
10/21/2024-12:04:55.334362  [**] [1:2010936:3] ET SCAN Suspicious inbound to Oracle SQL port 1521 [**] [Classification: Potentially Bad Traffic] [Priority: 2] {TCP} 192.168.56.101:50828 -> 192.168.56.110:1521
10/21/2024-12:10:36.290177  [**] [1:2100366:8] GPL ICMP PING *NIX [**] [Classification: Misc activity] [Priority: 3] {ICMP} 192.168.56.110:8 -> 192.168.56.101:0
10/21/2024-12:10:37.348034  [**] [1:2100366:8] GPL ICMP PING *NIX [**] [Classification: Misc activity] [Priority: 3] {ICMP} 192.168.56.110:8 -> 192.168.56.101:0
10/21/2024-12:10:38.372077  [**] [1:2100366:8] GPL ICMP PING *NIX [**] [Classification: Misc activity] [Priority: 3] {ICMP} 192.168.56.110:8 -> 192.168.56.101:0
10/21/2024-12:19:24.034310  [**] [1:2010937:3] ET SCAN Suspicious inbound to mySQL port 3306 [**] [Classification: Potentially Bad Traffic] [Priority: 2] {TCP} 192.168.56.101:61161 -> 192.168.56.110:3306
10/21/2024-12:19:24.034311  [**] [1:2010937:3] ET SCAN Suspicious inbound to mySQL port 3306 [**] [Classification: Potentially Bad Traffic] [Priority: 2] {TCP} 192.168.56.101:61161 -> 192.168.56.110:3306
10/21/2024-12:19:24.041692  [**] [1:2010939:3] ET SCAN Suspicious inbound to PostgreSQL port 5432 [**] [Classification: Potentially Bad Traffic] [Priority: 2] {TCP} 192.168.56.101:61161 -> 192.168.56.110:5432
10/21/2024-12:19:24.038058  [**] [1:2002911:6] ET SCAN Potential VNC Scan 5900-5920 [**] [Classification: Attempted Information Leak] [Priority: 2] {TCP} 192.168.56.101:61161 -> 192.168.56.110:5910
10/21/2024-12:19:24.042709  [**] [1:2002911:6] ET SCAN Potential VNC Scan 5900-5920 [**] [Classification: Attempted Information Leak] [Priority: 2] {TCP} 192.168.56.101:61161 -> 192.168.56.110:5904
10/21/2024-12:19:24.043689  [**] [1:2010936:3] ET SCAN Suspicious inbound to Oracle SQL port 1521 [**] [Classification: Potentially Bad Traffic] [Priority: 2] {TCP} 192.168.56.101:61161 -> 192.168.56.110:1521
10/21/2024-12:19:24.041693  [**] [1:2010939:3] ET SCAN Suspicious inbound to PostgreSQL port 5432 [**] [Classification: Potentially Bad Traffic] [Priority: 2] {TCP} 192.168.56.101:61161 -> 192.168.56.110:5432
10/21/2024-12:19:24.051433  [**] [1:2010935:3] ET SCAN Suspicious inbound to MSSQL port 1433 [**] [Classification: Potentially Bad Traffic] [Priority: 2] {TCP} 192.168.56.101:61161 -> 192.168.56.110:1433
10/21/2024-12:19:24.051433  [**] [1:2010935:3] ET SCAN Suspicious inbound to MSSQL port 1433 [**] [Classification: Potentially Bad Traffic] [Priority: 2] {TCP} 192.168.56.101:61161 -> 192.168.56.110:1433
10/21/2024-12:19:24.051433  [**] [1:2002910:6] ET SCAN Potential VNC Scan 5800-5820 [**] [Classification: Attempted Information Leak] [Priority: 2] {TCP} 192.168.56.101:61161 -> 192.168.56.110:5801
10/21/2024-12:19:24.043689  [**] [1:2010936:3] ET SCAN Suspicious inbound to Oracle SQL port 1521 [**] [Classification: Potentially Bad Traffic] [Priority: 2] {TCP} 192.168.56.101:61161 -> 192.168.56.110:1521
10/21/2024-12:19:24.043692  [**] [1:2002910:6] ET SCAN Potential VNC Scan 5800-5820 [**] [Classification: Attempted Information Leak] [Priority: 2] {TCP} 192.168.56.101:61161 -> 192.168.56.110:5802
10/21/2024-12:20:05.455508  [**] [1:2010937:3] ET SCAN Suspicious inbound to mySQL port 3306 [**] [Classification: Potentially Bad Traffic] [Priority: 2] {TCP} 192.168.56.101:49339 -> 192.168.56.110:3306
10/21/2024-12:20:05.455509  [**] [1:2010937:3] ET SCAN Suspicious inbound to mySQL port 3306 [**] [Classification: Potentially Bad Traffic] [Priority: 2] {TCP} 192.168.56.101:49339 -> 192.168.56.110:3306
10/21/2024-12:20:05.456326  [**] [1:2010936:3] ET SCAN Suspicious inbound to Oracle SQL port 1521 [**] [Classification: Potentially Bad Traffic] [Priority: 2] {TCP} 192.168.56.101:49339 -> 192.168.56.110:1521
10/21/2024-12:20:05.456325  [**] [1:2010936:3] ET SCAN Suspicious inbound to Oracle SQL port 1521 [**] [Classification: Potentially Bad Traffic] [Priority: 2] {TCP} 192.168.56.101:49339 -> 192.168.56.110:1521
10/21/2024-12:20:05.474991  [**] [1:2010935:3] ET SCAN Suspicious inbound to MSSQL port 1433 [**] [Classification: Potentially Bad Traffic] [Priority: 2] {TCP} 192.168.56.101:49339 -> 192.168.56.110:1433
10/21/2024-12:20:05.474991  [**] [1:2010935:3] ET SCAN Suspicious inbound to MSSQL port 1433 [**] [Classification: Potentially Bad Traffic] [Priority: 2] {TCP} 192.168.56.101:49339 -> 192.168.56.110:1433
10/21/2024-12:20:05.483688  [**] [1:2010939:3] ET SCAN Suspicious inbound to PostgreSQL port 5432 [**] [Classification: Potentially Bad Traffic] [Priority: 2] {TCP} 192.168.56.101:49339 -> 192.168.56.110:5432
10/21/2024-12:20:05.483687  [**] [1:2010939:3] ET SCAN Suspicious inbound to PostgreSQL port 5432 [**] [Classification: Potentially Bad Traffic] [Priority: 2] {TCP} 192.168.56.101:49339 -> 192.168.56.110:5432
10/21/2024-12:20:28.898174  [**] [1:2010937:3] ET SCAN Suspicious inbound to mySQL port 3306 [**] [Classification: Potentially Bad Traffic] [Priority: 2] {TCP} 192.168.56.101:34716 -> 192.168.56.110:3306
10/21/2024-12:20:28.898154  [**] [1:2010937:3] ET SCAN Suspicious inbound to mySQL port 3306 [**] [Classification: Potentially Bad Traffic] [Priority: 2] {TCP} 192.168.56.101:34716 -> 192.168.56.110:3306
10/21/2024-12:20:28.926865  [**] [1:2002911:6] ET SCAN Potential VNC Scan 5900-5920 [**] [Classification: Attempted Information Leak] [Priority: 2] {TCP} 192.168.56.101:45214 -> 192.168.56.110:5902
10/21/2024-12:20:28.926864  [**] [1:2002911:6] ET SCAN Potential VNC Scan 5900-5920 [**] [Classification: Attempted Information Leak] [Priority: 2] {TCP} 192.168.56.101:45214 -> 192.168.56.110:5902
10/21/2024-12:20:28.953593  [**] [1:2002910:6] ET SCAN Potential VNC Scan 5800-5820 [**] [Classification: Attempted Information Leak] [Priority: 2] {TCP} 192.168.56.101:43542 -> 192.168.56.110:5810
10/21/2024-12:20:28.953586  [**] [1:2002910:6] ET SCAN Potential VNC Scan 5800-5820 [**] [Classification: Attempted Information Leak] [Priority: 2] {TCP} 192.168.56.101:43542 -> 192.168.56.110:5810
10/21/2024-12:20:28.955098  [**] [1:2010936:3] ET SCAN Suspicious inbound to Oracle SQL port 1521 [**] [Classification: Potentially Bad Traffic] [Priority: 2] {TCP} 192.168.56.101:34636 -> 192.168.56.110:1521
10/21/2024-12:20:28.955098  [**] [1:2010936:3] ET SCAN Suspicious inbound to Oracle SQL port 1521 [**] [Classification: Potentially Bad Traffic] [Priority: 2] {TCP} 192.168.56.101:34636 -> 192.168.56.110:1521
10/21/2024-12:20:28.966066  [**] [1:2010939:3] ET SCAN Suspicious inbound to PostgreSQL port 5432 [**] [Classification: Potentially Bad Traffic] [Priority: 2] {TCP} 192.168.56.101:46826 -> 192.168.56.110:5432
10/21/2024-12:20:28.966065  [**] [1:2010939:3] ET SCAN Suspicious inbound to PostgreSQL port 5432 [**] [Classification: Potentially Bad Traffic] [Priority: 2] {TCP} 192.168.56.101:46826 -> 192.168.56.110:5432
10/21/2024-12:20:28.967456  [**] [1:2010935:3] ET SCAN Suspicious inbound to MSSQL port 1433 [**] [Classification: Potentially Bad Traffic] [Priority: 2] {TCP} 192.168.56.101:54662 -> 192.168.56.110:1433
10/21/2024-12:20:28.967455  [**] [1:2010935:3] ET SCAN Suspicious inbound to MSSQL port 1433 [**] [Classification: Potentially Bad Traffic] [Priority: 2] {TCP} 192.168.56.101:54662 -> 192.168.56.110:1433

```

### Задание 2

В логе fail2ban мы видим атаку со стороны хоста 192.168.56.101 по ssh, после нескольких подключение ip уходит в бан.

```
2024-10-21 13:20:01,544 fail2ban.server         [4717]: INFO    Starting Fail2ban v1.1.0
2024-10-21 13:20:01,544 fail2ban.observer       [4717]: INFO    Observer start...
2024-10-21 13:20:01,554 fail2ban.database       [4717]: INFO    Connected to fail2ban persistent database '/var/lib/fail2ban/fail2ban.sqlite3'
2024-10-21 13:20:01,554 fail2ban.jail           [4717]: INFO    Creating new jail 'sshd'
2024-10-21 13:20:01,662 fail2ban.jail           [4717]: INFO    Jail 'sshd' uses systemd {}
2024-10-21 13:20:01,662 fail2ban.jail           [4717]: INFO    Initiated 'systemd' backend
2024-10-21 13:20:01,663 fail2ban.filter         [4717]: INFO      maxLines: 1
2024-10-21 13:20:01,683 fail2ban.filtersystemd  [4717]: INFO    [sshd] Added journal match for: '_SYSTEMD_UNIT=ssh.service + _COMM=sshd'
2024-10-21 13:20:01,683 fail2ban.filter         [4717]: INFO      maxRetry: 5
2024-10-21 13:20:01,683 fail2ban.filter         [4717]: INFO      findtime: 600
2024-10-21 13:20:01,684 fail2ban.actions        [4717]: INFO      banTime: 600
2024-10-21 13:20:01,684 fail2ban.filter         [4717]: INFO      encoding: UTF-8
2024-10-21 13:20:01,685 fail2ban.jail           [4717]: INFO    Jail 'sshd' started
2024-10-21 13:20:01,685 fail2ban.filtersystemd  [4717]: INFO    [sshd] Jail is in operation now (process new journal entries)
2024-10-21 13:21:04,103 fail2ban.filter         [4717]: INFO    [sshd] Found 192.168.56.101 - 2024-10-21 13:21:03
2024-10-21 13:21:04,105 fail2ban.filter         [4717]: INFO    [sshd] Found 192.168.56.101 - 2024-10-21 13:21:04
2024-10-21 13:21:06,572 fail2ban.filter         [4717]: INFO    [sshd] Found 192.168.56.101 - 2024-10-21 13:21:06
2024-10-21 13:21:10,322 fail2ban.filter         [4717]: INFO    [sshd] Found 192.168.56.101 - 2024-10-21 13:21:09
2024-10-21 13:21:14,067 fail2ban.filter         [4717]: INFO    [sshd] Found 192.168.56.101 - 2024-10-21 13:21:13
2024-10-21 13:21:14,309 fail2ban.actions        [4717]: NOTICE  [sshd] Ban 192.168.56.101
```
