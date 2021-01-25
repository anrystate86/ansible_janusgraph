# ansible_janusgraph

Ansible playbook for installing standalone server janusgraph with cassandra cluster and elasticsearch claster

Playbook using roles ansible-cassandra (https://github.com/wireapp/ansible-cassandra) and ansible-elasticsearch (https://github.com/elastic/ansible-elasticsearch)

Плейбук ansible, для развертывания стендалона janusgraph кластеров cassandra(в примере 3 ноды) и elasticsearch (1 master нода, 2 data ноды)

В плейбуке использованы роли ansible-cassandra (https://github.com/wireapp/ansible-cassandra) и ansible-elasticsearch (https://github.com/elastic/ansible-elasticsearch)

Протестировано на ВМ на базе Centos7, 2 CPU, RAM 4G


Выбор ВМ на которых будут установлены сервисы производится в файле inventory

Плейбук для запуска развертывания install_cluster.yml

Перед развертыванием рекомендуется проверить настройки запуска ролей в плейбуке.

Роль prereqisites предназначена для установки необходимых приложений, а так же при установке переменной "pre_dns: false" позволяет при отсутствии dns-сервера добавлять ip-адреса серверов в файл /etc/hosts

Роли ansible и cassandra используют параметры позволяющие автоматически сформировать кластеры, 

- для роли ansible рекомендуется изменять параметр "es_heap_size: "512m"" в соответствии с требованиями производительности

- установка параметров сетевых подключений производится из файла инвентори

Роль janusgraph предназначена для установки стендалона janusgraph, с настройками на развернутые кластеры cassandra и elasticsearch. Запуск janusgraph реализован в качестве 
службы systemd с использованием модифицированного файла janusgraph.sh из -full поставки janusgraph. 


