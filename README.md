# DNSHW
Домашнее задание на тему "Работа с DNS"
Задание:
Что нужно сделать?
- взять стенд https://github.com/erlong15/vagrant-bind
- добавить еще один сервер client2
- завести в зоне dns.lab
- имена
- web1 - смотрит на клиент1
- web2 смотрит на клиент2
- завести еще одну зону newdns.lab
- завести в ней запись
- www - смотрит на обоих клиентов
- настроить split-dns
- клиент1 - видит обе зоны, но в зоне dns.lab только web1
- клиент2 видит только dns.lab
Для начала устанавливаем сервисы для выполнения нашего ДЗ: Vagrant, Ansible, Virtualbox
Установка Vagrant:
wget -O - https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(grep -oP '(?<=UBUNTU_CODENAME=).*' /etc/os-release || lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
sudo apt update && sudo apt install vagrant
Установка Ansible:
apt install software-properties-common
add-apt-repository --yes --update ppa:ansible/ansible
apt install ansible
Установка Virtualbox:
apt install virtualbox
После установки пишем наши скрипты и Vagrantfile.
Делаем запуск и проверяем работу нашей сети.
На client:
ping web1.dns.lab
На client2:
ping web1.dns.lab
ping web2.dns.lab
ping www.newdns.lab
Если всё работает – задание выполнено.
