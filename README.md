
### Задание: Обновление ядра системы ###

1. Запустите ВМ c Ubuntu.
2. Обновите ядро ОС на новейшую стабильную версию из mainline-репозитория.
3. Оформите отчет в README-файле в GitHub-репозитории.

   ##выполнение задания##

   Проверяем текущую версию ядра

```bash 

sadmin@lp-ubn4:~$ uname -r
6.8.0-59-generic

sadmin@lp-ubn4:~$ uname -p
x86_64
```
> [!NOTE]
> изначально взял ядро 6.19.11 но с нм были проблемы решить которые не смог.
> в итоге попробовал 6.18.20 с ним все получилось

Создаем папку и скачиваем в нее файлы пакетов
```bash
sadmin@lp-ubn4:~$ mkdir update_core && cd update_core
sadmin@lp-ubn4:~/update_core$
wget https://kernel.ubuntu.com/mainline/v6.18.20/amd64/linux-headers-6.18.20-061820-generic_6.18.20-061820.202603251312_amd64.deb
wget https://kernel.ubuntu.com/mainline/v6.18.20/amd64/linux-headers-6.18.20-061820_6.18.20-061820.202603251312_all.deb
wget https://kernel.ubuntu.com/mainline/v6.18.20/amd64/linux-image-unsigned-6.18.20-061820-generic_6.18.20-061820.202603251312_amd64.deb
wget https://kernel.ubuntu.com/mainline/v6.18.20/amd64/linux-modules-6.18.20-061820-generic_6.18.20-061820.202603251312_amd64.deb
```
Запускаем установку сразу всех пакетов
```bash
 sudo dpkg -i *.deb
```
Проверяем, что появилось новое ядро
```bash
sadmin@lp-ubn4:~/update_core$ ls -al /boot
total 203084
drwxr-xr-x  4 root root     4096 Apr  5 17:45 .
drwxr-xr-x 23 root root     4096 Apr  5 16:39 ..
-rw-r--r--  1 root root   304142 Mar 25 13:12 config-6.18.20-061820-generic
-rw-r--r--  1 root root   287601 Mar 13 13:27 config-6.8.0-107-generic
drwxr-xr-x  5 root root     4096 Apr  5 17:45 grub
lrwxrwxrwx  1 root root       33 Apr  5 17:44 initrd.img -> initrd.img-6.18.20-061820-generic
-rw-r--r--  1 root root 79579611 Apr  5 17:45 initrd.img-6.18.20-061820-generic
-rw-r--r--  1 root root 76274843 Apr  5 16:57 initrd.img-6.8.0-107-generic
lrwxrwxrwx  1 root root       28 Apr  5 16:38 initrd.img.old -> initrd.img-6.8.0-107-generic
drwx------  2 root root    16384 Apr  5 16:28 lost+found
-rw-------  1 root root 10559938 Mar 25 13:12 System.map-6.18.20-061820-generic
-rw-------  1 root root  9125925 Mar 13 13:27 System.map-6.8.0-107-generic
lrwxrwxrwx  1 root root       30 Apr  5 17:44 vmlinuz -> vmlinuz-6.18.20-061820-generic
-rw-------  1 root root 16732672 Mar 25 13:12 vmlinuz-6.18.20-061820-generic
-rw-------  1 root root 15042952 Mar 13 17:46 vmlinuz-6.8.0-107-generic
lrwxrwxrwx  1 root root       25 Apr  5 16:38 vmlinuz.old -> vmlinuz-6.8.0-107-generic
```

Перезагрузились, проверяем версию ядра
```
sadmin@lp-ubn4:~$ uname -r
6.18.20-061820-generic
```


