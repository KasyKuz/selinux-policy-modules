В данном репозитории размещены примеры трех модулей SELinux, каждый из них реализует определенный функционал:

*module_1.te - Запрет создания символических ссылок (symlinks) в системных директориях
*module_2.te - Запрет выполнения утилит `ifconfig` и `mount` для домена `unconfined_t`
*module_3.te - Запрет создания жестких ссылок 

Для сборки и приминения каждого из модулей, необходимо выполнить следующие действия:
```bash
checkmodule -M -m -o module_1.mod module_1.te
semodule_package -o module_1.pp -m module_1.mod
sudo semodule -i module_1.pp
```

Модули необходимо тестировать в режиме Enfrosing, для этого ноебходимо выполнить: `sudo setenforce 1`

Удалить модули можно с помощью команды: `sudo semodule -r module_1`
