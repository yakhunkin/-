Яхункин К-ИСП 39-1 
Лабораторная работа

![image](https://github.com/user-attachments/assets/c04e333d-d7cf-47dd-b5c8-1c774e8843d1)



Установили Oracle linux
Установили гостевые дополнения по инструкции: 
[инструкция для VBoxGA.docx](https://github.com/user-attachments/files/18921020/VBoxGA.docx)
Далее выполняем команды
`sudo yum install wget` 

![image](https://github.com/user-attachments/assets/417f85d3-2a1c-4f9e-9280-b7c0e27d61a2)

Далее вводим команду для установки утилиты
`sudo yum install curl`

![image](https://github.com/user-attachments/assets/fa9e539b-01f3-4b15-800c-f7ee97abd34b)


Далее скачиваем репозиторий
`sudo wget -P /etc/yum.repos.d/ https://download.docker.com/linux/centos/docker-ce.repo`

![image](https://github.com/user-attachments/assets/696bb008-dfe3-48e8-aa6a-ccc71beafc14)

устанавливаем docker
`sudo yum install docker-ce docker-ce-cli containerd.io`

![image](https://github.com/user-attachments/assets/6971313d-55f8-4d21-8665-7b90fc06590f)

Запускаем и разрешаем автозапуск
`sudo systemctl enable docker --now`

![image](https://github.com/user-attachments/assets/6d53d112-b3a4-4849-a365-c9434deba32e)

Получаем номер последней версии Docker Compose и сохраняем его в переменную COMVER
`COMVER=$(curl -s https://api.github.com/repos/docker/compose/releases/latest | grep 'tag_name' | cut -d\" -f4)`

![image](https://github.com/user-attachments/assets/50d00f7d-ae97-433d-8448-dd24cbf7e65d)

вводим команду для копирования репозитория
`git clone https://github.com/skl256/grafana_stack_for_docker.git`

![image](https://github.com/user-attachments/assets/4f1afdb3-afcf-4416-aeff-b76d1e347ce6)

Выдает ошибку вводим команду и со всем соглашаемся 
`sudo yum install git-core`
после снова вводим команду выше

![image](https://github.com/user-attachments/assets/55908990-5fff-4313-82d9-4bf2f00a3170)

переходим в другую папку
`cd grafana_stack_for_docker`

![image](https://github.com/user-attachments/assets/28d6c339-3150-4d78-b5de-13e942fce7b1)

создаем новый дерикторий
`sudo mkdir -p /mnt/common_volume/swarm/grafana/config`
![image](https://github.com/user-attachments/assets/95c16f2e-2b2f-4bf4-9103-cab01e94b8d1)

создаем директории для хранения данных Grafana и Prometheus
`sudo mkdir -p /mnt/common_volume/grafana/{grafana-config,grafana-data,prometheus-data}`

![image](https://github.com/user-attachments/assets/02c12b87-adba-4621-b77e-1b1b943ba33f)

создаём пустой файл с именем `grafana.ini` в указанном каталоге, если такого файла ещё нет.  Если файл уже существует, команда ничего не делает.

`touch /mnt/common_volume/grafana/grafana-config/grafana.ini`

![image](https://github.com/user-attachments/assets/ddb2eb57-2479-4e04-b660-6c73188ca9a6)

копируем все файлы и подкаталоги из каталога `config/` в каталог `/mnt/common_volume/swarm/grafana/config/`
`cp config/* /mnt/common_volume/swarm/grafana/config/`

![image](https://github.com/user-attachments/assets/f6974cb4-3543-4fe4-874f-9923320685a9)

переименовываем файл `grafana.yaml` в `docker-compose.yaml`
`mv grafana.yaml docker-compose.yaml`

![image](https://github.com/user-attachments/assets/3d807014-56ef-49b4-8e32-b63305198228)

поднимаем Docker Compose
`sudo docker compose up -d`

![image](https://github.com/user-attachments/assets/13d36e18-2036-48a6-8301-13939a7056a5)

![image](https://github.com/user-attachments/assets/27a49fc0-6177-48b9-84f7-344c1b22699c)

вводим команду `sudo vi docker-compose.yaml`и переходим в файл

![image](https://github.com/user-attachments/assets/a487d4e8-bc4c-4c9d-b14a-ffcebc4d3b43)

для того чтобы внести изменения нажимаем на клавиатуре insert
для того чтобы сохранить нажимаем Esc и вводим wp!
вводим `node-exporter` после слова `services`

![image](https://github.com/user-attachments/assets/381b43d5-bf2b-4986-a461-510eacd1e419)

открываем файл prometheus.yaml
`sudo vi prometheus.yaml`
и меняем там /mnt/common_volume/swarm/grafana/config/prometheus.yaml -  на exporter:9100

Далее переходим на работу с Grafana
переходим на сайт localhost:3000. - Пользователь и пароль: admin. - Код графаны 1816. - Код прометеуса: http://prometheus:9090.

![image](https://github.com/user-attachments/assets/d29cf7a6-17e6-4dec-8ec9-4bab9042a95a)


Создаем новый Dashboard

![image](https://github.com/user-attachments/assets/a6ca9283-f832-4a36-9f20-2d70c4e97e04)

Далее создаем визуализацию

![image](https://github.com/user-attachments/assets/3a1c545e-dd4f-4b31-9104-4b01e0021932)

 нажимаем на данную кнопку 
 
 ![image](https://github.com/user-attachments/assets/88612c4f-0d78-48ec-bd28-501260fd0d36)

 из предоставленного меню выбираем Prometheus
 ![image](https://github.com/user-attachments/assets/16011d77-5f71-4432-81b9-831c8fe6c8ec)

 вставляем код прометеуса
 ![image](https://github.com/user-attachments/assets/c77c799a-54a0-4a1f-938d-ed9a357bcdca)

 в разделе authentication меняем `No authentication` на `basic authentication`
 
![image](https://github.com/user-attachments/assets/d06d4bb1-31b7-4134-96da-1ad69f3f585f)

сохраняем и смотри все ли хорошо 
![image](https://github.com/user-attachments/assets/967a704c-572d-42ae-b128-5ae825ec659b)

возвращаемся на пару шагов назад и нажимаем вместо `Add visualisation`   `import`

и вводим 

![image](https://github.com/user-attachments/assets/167d4d85-c661-4a78-a389-a11474759266)

далее выбираем import

![image](https://github.com/user-attachments/assets/16f0b5c2-882f-4871-be5a-0bae49f5d6eb)

далее видим результат
![image](https://github.com/user-attachments/assets/71caad82-8c2a-4a70-bfda-97dc409024ad)


Далее пойдет работа с Victoria Metrics
Для начала необходимо изменить файл `docker-compose.yaml`
для этого переходим в каталог `grafana_stack_for_docker`
вводим команду `cd grafana_stack_for_docker`

![image](https://github.com/user-attachments/assets/dde82ff9-3895-4ff0-8704-8660fbe7280d)

далее открываем файл 
`sudo vi docker compose.yaml`























