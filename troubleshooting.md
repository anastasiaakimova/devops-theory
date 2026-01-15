| Категория | Инструмент / проблема | Описание / команды |
|----------|----------------------|--------------------|
| **Диск<br>Disk** | **df** — Disk space problems | `df -h` — disk usage (human readable)<br>`df -i` — inode usage<br><br>`du -sh /tmp` — size of directory<br>`du -sh /var/log/*` |
| | **iostat** — Disk IO problems | `iostat` — read/write statistics<br>`iotop` — which processes use disk IO |
| **Процессор<br>CPU** | **top** — CPU & process issues | `top` — load average, process time, memory<br><br>`%Cpu(s):`<br>`us` — user processes<br>`sy` — system processes<br>`ni` — nice processes<br>`id` — idle<br>`wa` — IO wait<br>`hi` — hardware IRQ<br>`si` — software IRQ<br>`st` — steal time |
| | **htop** — CPU & process issues | **Shortcuts:**<br>`F6` — sorting<br>`F4` — filtering<br>`F9` — kill process<br>`F5` — tree view of processes <br>`F2` — threads<br><br>**Columns:**<br>`PID` — process ID<br>`USER` — owner<br>`PRI / NI` — priority<br>`CPU%` — CPU usage<br>`MEM%` — memory usage<br>`VIRT / RES / SHR` — memory types<br>`S` — state<br>`COMMAND` — command |
| | **Process states** | `R` — running<br>`S` — sleeping<br>`D` — uninterruptible sleep (disk/network)<br>`Z` — zombie<br>`T` — stopped<br><br> Many `D` → check `iostat` |
| **Память<br>Memory** | **free** — Memory problems | `free -h` — memory usage |
| | **vmstat** — Memory problems | `vmstat` — real-time memory & IO |
| **Сеть<br>Network** | **tcpdump** | `tcpdump -i eth0`<br>`tcpdump -i eth0 port 443`<br>`tcpdump -i eth0 host 10.0.1.15`<br>`tcpdump -i eth0 -A port 80` |
| | **dig — DNS problems** | `dig example.com`<br>`dig example.com @8.8.8.8`<br>`dig example.com A`<br>`dig example.com CNAME`<br>`dig example.com MX` |
| | **nslookup — DNS problems** | |
| | **netstat** | |
| | **ss** | |
| | **ip a** | |
| | **ifconfig** | |
| | **ping** | |
| | **curl** | |
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

```
inode - It is a data structure in Unix-like file systems (Linux, macOS), 
a file "passport" that stores metadata (information about the file, not the data itself) such as size, owner, 
access rights, creation/modification time, and pointers to physical data blocks on disk, 
but not the file name. which is stored separately. 
    
Each file, directory, or object in the system has its own unique inode, and if they run out, new files 
cannot be created, even if there is free space.

Each time a new file is created, it is provided with an inode number and a name, 
after which it is saved as unique entries in the directory. 
It is important to remember here that one of the ways to exhaust free space on the file system is to use all Inodes. 
This means that even if you have free disk space, you still won't be able to create a new file. 
When all the Inodes in your system are in use, it can cause the system to suddenly stop.

The number of inodes on the disk is static. 
This means that if you have a lot of files, the inodes may run out before the disk space runs out. 
As soon as the file system runs out, all new files and folders will be rejected. 
There will be no negative consequences until then. 
When inodes is 100% used, you will start to notice:

- Data loss
- Application failures
- Restarting the OS
- Failure to restart processes
- Periodic tasks will not be performed.

There are two types of inode quotas: soft and hard. 
If you exceed the soft quota, you will still be able to create files. 
If you exceed the limit, you won't be able to.

Many functions of your hosting account require the creation of files. 
If you exceed the hard limit, you will not be able to add new web pages, receive emails, 
install software, or perform many familiar tasks.

It is better to reduce inode usage by deleting files long before you reach the hard limit.

```

## The "out of inodes" problem is
**Symptom:** It is impossible to create new files or directories, although there is still disk space.

**Reason:** Thousands of small files are created (for example, in the cache or logs), which quickly "eat up" all available inodes.

**Solution:** Deleting files (especially small ones) or archiving them, expanding the disk, or reformatting to accommodate a larger number of inodes.


Use the `df -i` command (on Linux) to check the usage of the inodes.


## Literature
- https://habr.com/ru/articles/462849/
- https://hostpro.ua/blog/what-is-inodes/#:~:text=%D0%BA%D0%BE%D1%82%D0%BE%D1%80%D0%BE%D0%B9%20%D0%BC%D1%8B%20%D0%BD%D0%B0%D1%87%D0%B0%D0%BB%D0%B8.-,%D0%A7%D1%82%D0%BE%20%D1%82%D0%B0%D0%BA%D0%BE%D0%B5%20%D0%B8%D0%BD%D0%BE%D0%B4?,%D0%BD%D0%BE%20%D0%BD%D0%B5%20%D0%BF%D1%83%D1%82%D1%8C%20%D0%BA%20%D1%84%D0%B0%D0%B9%D0%BB%D1%83).