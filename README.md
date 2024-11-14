# ещё одна (возможно неудачная) попытка что-то создать

Перед началой установки, нужно установить Linux Oracle на VirtualBox, для этого нужно:

Иметь образ Linux Выделить 2+ ядер. Выделать 4096+ МБ оперативы. При установки операционной системы, нужно будет выбрать английский язык.

Далее переходим к установке docker с использованием grafana, вводим следующий набор команд:
1. sudo yum install wget
• устанавливает утилиту wget на вашу систему

![Alt 1.png](https://github.com//hzkov/3/blob/main/1.jpg)

2. sudo wget -P /etc/yum.repos.d/ https://download.docker.com/linux/centos/docker-ce.repo

• Скачиваем файл репозитория

[3.jpg](https://github.com/hzkov/3/blob/main/Images/3.jpg)

3.sudo yum install docker-ce docker-ce-cli containerd.io

• Устанавливаем docker



4.sudo systemctl enable docker --now

• Запускаем его и разрешаем автозапуск

5.sudo yum install curl

• Для этого сначала убедимся в наличие пакета curl

COMVER=$(curl -s https://api.github.com/repos/docker/compose/releases/latest | grep 'tag_name' | cut -d\" -f4)

• Объявление переменной COMVER, полученной в результате curl запроса, хранящей в себе номер последней версии Docker Compose

[4.jpg](https://github.com/hzkov/3/blob/main/Images/4.jpg)
