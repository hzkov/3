# ещё одна (возможно неудачная) попытка что-то создать

Перед началой установки, нужно установить Linux Oracle на VirtualBox, для этого нужно:

Иметь образ Linux Выделить 2+ ядер. Выделать 4096+ МБ оперативы. При установки операционной системы, нужно будет выбрать английский язык.

Далее переходим к установке docker с использованием grafana, вводим следующий набор команд:
1. sudo yum install wget
• устанавливает утилиту wget на вашу систему

![Alt 1.png](https://github.com//hzkov/3/blob/main/1.jpg)

2. sudo wget -P /etc/yum.repos.d/ https://download.docker.com/linux/centos/docker-ce.repo

• Скачиваем файл репозитория

![3.jpg](https://github.com/hzkov/3/blob/main/Images/3.jpg)

3. sudo yum install docker-ce docker-ce-cli containerd.io

• Устанавливаем docker

![Alt 6.png](https://github.com//hzkov/3/blob/main/6.jpg)

4. sudo systemctl enable docker --now

• Запускаем его и разрешаем автозапуск

5. sudo yum install curl

• Для этого сначала убедимся в наличие пакета curl

6. COMVER=$(curl -s https://api.github.com/repos/docker/compose/releases/latest | grep 'tag_name' | cut -d\" -f4)

• Объявление переменной COMVER, полученной в результате curl запроса, хранящей в себе номер последней версии Docker Compose

![4.jpg](https://github.com/hzkov/3/blob/main/Images/4.jpg)

7. sudo curl -L "https://github.com/docker/compose/releases/download/$COMVER/docker-compose-$(uname -s)-$(uname -m)" -o /usr/bin/docker-compose

• Теперь скачиваем скрипт docker-compose последней версии, используя объявленную ранее переменную и помещаем его в каталог /usr/bin
![Alt 5](https://github.com//hzkov/3/blob/main/5.jpg)
8. sudo chmod +x /usr/bin/docker-compose

• Предоставление прав на выполнение файла docker-compose.

9. docker-compose --version

• Проверка установленной версии Docker Compose.



• Можно скачать git прямо из командной строки прописав Y

10. git clone https://github.com/skl256/grafana_stack_for_docker.git

• выдаст ошибку и предложит скачать git, согласиться и продолжить

11. cd grafana_stack_for_docker

• переход в папку

12. sudo mkdir -p /mnt/common_volume/swarm/grafana/config

• команда создаёт полный путь /mnt/common_volume/swarm/grafana/config, включая все необходимые промежуточные каталоги, если они ещё не существуют.

13. sudo mkdir -p /mnt/common_volume/grafana/{grafana-config,grafana-data,prometheus-data}

• команда создаёт структуру каталогов для Grafana и связанных с ней компонентов, если они ещё не существуют.

14. sudo chown -R $(id -u):$(id -g) {/mnt/common_volume/swarm/grafana/config,/mnt/common_volume/grafana}

• все файлы и каталоги в указанных директориях будут переданы в собственность текущему пользователю и его группе

15. touch /mnt/common_volume/grafana/grafana-config/grafana.ini

• файл grafana.ini уже существует, команда обновит его временные метки (время последнего доступа и изменения). Если файл не существует, команда создаст новый пустой файл с указанным именем по указанному пути.

16. cp config/* /mnt/common_volume/swarm/grafana/config/

• команда копирует все файлы и подкаталоги из директории config в директорию /mnt/common_volume/swarm/grafana/config/

17. mv grafana.yaml docker-compose.yaml 

• команда переименовывает файл grafana.yaml в docker-compose.yaml. Ничего не покажет, но можно проверить при помощи команды ls

18. sudo docker compose up -d

• команда создает и запускает контейнеры в фоновом режиме, используя конфигурацию из файла docker-compose.yml, с правами суперпользователя.





