
### Задание: Обновление ядра системы ###

1. Запустите ВМ c Ubuntu.
2. Обновите ядро ОС на новейшую стабильную версию из mainline-репозитория.
3. Оформите отчет в README-файле в GitHub-репозитории.

   ##выполнение задания##

   Проверяем текущую версию ядра

```bash 

sadmin@lp-ubn2:~$ uname -r
6.8.0-59-generic

sadmin@lp-ubn2:~$ uname -p
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

