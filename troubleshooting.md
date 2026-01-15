| Категория | Инструмент / проблема | Описание / команды |
|----------|----------------------|--------------------|
| **Диск<br>Disk** | **df** — Disk space problems | `df -h` — disk usage (human readable)<br>`df -i` — inode usage<br><br>`du -sh /tmp` — size of directory<br>`du -sh /var/log/*` |
| | **iostat** — Disk IO problems | `iostat` — read/write statistics<br>`iotop` — which processes use disk IO |
| **Процессор<br>CPU** | **top** — CPU & process issues | `top` — load average, process time, memory<br><br>`%Cpu(s):`<br>`us` — user processes<br>`sy` — system processes<br>`ni` — nice processes<br>`id` — idle<br>`wa` — IO wait<br>`hi` — hardware IRQ<br>`si` — software IRQ<br>`st` — steal time |
| | **htop** — CPU & process issues | **Shortcuts:**<br>`F6` — sorting<br>`F4` — filtering<br>`F9` — kill process<br>`F5` — tree view<br>`F2` — threads<br><br>**Columns:**<br>`PID` — process ID<br>`USER` — owner<br>`PRI / NI` — priority<br>`CPU%` — CPU usage<br>`MEM%` — memory usage<br>`VIRT / RES / SHR` — memory types<br>`S` — state<br>`COMMAND` — command |
| | **Process states** | `R` — running<br>`S` — sleeping<br>`D` — uninterruptible sleep (disk/network)<br>`Z` — zombie<br>`T` — stopped<br><br>⚠️ Many `D` → check `iostat` |
| **Память<br>Memory** | **free** — Memory problems | `free -h` — memory usage |
| | **vmstat** — Memory problems | `vmstat` — real-time memory & IO |
| **Сеть<br>Network** | **tcpdump** | `tcpdump -i eth0` — capture traffic<br>`tcpdump -i eth0 port 443`<br>`tcpdump -i eth0 host 10.0.1.15`<br>`tcpdump -i eth0 -A port 80` |
| | **dig** — DNS problems | `dig example.com`<br>`dig example.com @8.8.8.8`<br>`dig example.com A`<br>`dig example.com CNAME`<br>`dig example.com MX` |
| | **nslookup** — DNS problems | `nslookup example.com`<br>`nslookup example.com 1.1.1.1` |
| | **Network utils** | `netstat -tulpn` — listening ports<br>`ss`<br>`ip a`<br>`ifconfig`<br>`ping`<br>`curl` |
| **Процессы<br>Processes** | **ps** | `ps aux` — user-oriented format<br>`ps -ef` — full format |
| **Логи<br>Logs** | **System logs** | `/var/log`<br>`tail -f -n50 /var/log/syslog`<br>`/var/log/auth.log`<br>`/var/log/kern.log`<br>`dmesg -T`<br>`journalctl` |


```
top
```

`us` — процент использования CPU пользовательскими процессами

`sy` — процент использования CPU системными процессами

`ni` — процент использования CPU процессами с изменённым приоритетом (nice)

`id` — процент времени простоя CPU

`wa` — процент времени, когда CPU ждёт завершения операций ввода-вывода

`hi` — Hardware IRQ (аппаратные прерывания)

`si` — Software Interrupts (программные прерывания)

`st` — Steal Time — ресурсы CPU, "заимствованные" гипервизором для других задач; на физических серверах равно нулю
