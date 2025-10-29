Ansible плэйбуки для установки PostgreSQL15, KSC + Web console на Debian 12.

Начало работы с ansible:
1) Установить ansible.
2) Перенести файлы на хост с ansible в папку ansible: ansible.cfg, hosts.txt, postgresql.yml, answers.txt, installksc.yml, installkscweb.yml.
3) Преднастроить файлы в соответвии с рекомендациями ниже.

ansible.cfg - ansible конфиг.

hosts.txt - файл для добавления хостов.

ansible-playbook <name>.yml - запуск плэйбука.

Устанавливать нужно в соответствии со следующим порядком:

1. postgresql.yml - добавление репозиториев PostgreSQL15, установка PostgreSQL, изменение конфигурационного файла PostgreSQL, а также создание БД kav, пользователя KSCAdmin в БД и назначение ему привилегий.
Настройка конфигурации PostgreSQL проводилась в соответсвии с документацией на сайте: https://support.kaspersky.com/KSCLinux/15.1/ru-RU/241223.htm

ansible-playbook postgresql.yml - запуск установки postgresql

answers.txt - файл автоответов, использующийся при установке ksc. Работает в совокупности с плэйбуком installksc.yml.
В данном файле необходимо отредактировать переменные для корректной установки Kaspersky Security Center Linux в тихом режиме.
Внутри текcтового документа содержатся комментарии для каждой переменной.

2. installksc.yml - создание пользователя ksc и группы kladmins, а также установка KSC.
В задании под названием "Скачать пакет установки KSC" изменить параметр в поле url, где указать ссылку для установки требуемой версии KSC.

ansible-playbook installksc.yml - запуск установки KSC

3. installkscweb.yml - устанавливает KSC Web console, а также создаёт учетную запись для работы с Kaspersky Security Center Web Console.
В задании "Создание учетной записи для работы с Kaspersky Security Center Web Console" указать необходимые учетные данные, которые в дальнейшем будут использоваться для работы с KSC Web Console.
В задании под названием "Загрузка пакета ksc-web-console" изменить параметр в поле url, где указать ссылку для установки требуемой версии KSC Web console.

ansible-playbook installkscweb.yml - запуск установки Web KSC