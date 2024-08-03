# NFS Server
## Устанавливаем и запускаем сервер
```
sudo apt install nfs-kernel-server
sudo systemctl start nfs-kernel-server.service
sudo chmod 777 -R /home
```

## Добавляем папку
Редактируем файл /etc/exports
```
sudo chown nobody:nogroup /home
/home *(rw,sync,root_squash,no_subtree_check)
```

```
exportfs -a
```

В Windows в PowerShell с правами администратора
```
Enable-WindowsOptionalFeature -FeatureName ServicesForNFS-ClientOnly, ClientForNFS-Infrastructure -Online -NoRestart
```
с пользовательскими правами
```
New-PSdrive -PSProvider FileSystem -Name Z -Root \\192.168.1.100\home -Persist
```
umount Z:

