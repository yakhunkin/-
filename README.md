Парамонов К-ИСП 39-1 
Лабораторная работа
Задание 1


Установили Oracle linux
![image](https://github.com/user-attachments/assets/244a15d8-2a4d-49ba-978a-0b4dac0069dc)

Установили гостевые дополнения по инструкции: 
[инструкция для VBoxGA.docx](https://github.com/user-attachments/files/18921020/VBoxGA.docx)

После выполнения команды 
`sudo yum install wget` 
Возникла ошибка, указывающая на отсутствие прав доступа (`is not in the sudoers file`).  Для решения проблемы необходимо войти в систему от имени суперпользователя с помощью команды `su`.
![image](https://github.com/user-attachments/assets/4a6df09a-9526-4368-8188-55702ef3aac6)

Этот промах указывает путь к команде 
`sudo vi /etc/sudoers`
которая генерирует конфигурационный файл.  В него добавлена строка `Larin ALL=(ALL) ALL` (проблемы могут возникнуть из-за необходимости нажатия Tab).  Для сохранения изменений и выхода из файла нужно нажать Shift + : и выполнить команду 
`wq!`.
![image](https://github.com/user-attachments/assets/18725e7a-5821-4e3b-9493-edbf1fe1f580)

![image](https://github.com/user-attachments/assets/11723064-3289-4039-925e-0ef8f7a5799b)

После всех этих операций снова вводим команду:
`sudo yum install wget`
А затем, чтобы проверить успешность загрузки, используем команду:
`wget --version`.
![image](https://github.com/user-attachments/assets/e48b7b1d-0098-4808-8265-342f9ca18389)

Задание 2
Прописываем команду 
sudo yum install curl 
Чтобы убедиться, что библиотека Curl скачана на виртуальную машину
![image](https://github.com/user-attachments/assets/703c91e3-9b56-4849-954e-963bfcf29862)

Далее в задании указываем команду 
`sudo wget -P /etc/yum.repos.d/ https://download.docker.com/linux/centos/docker-ce.repo` 
Эта команда добавляет репозиторий Docker по адресу `/etc/yum.repos.d/` в виртуальную машину.
![image](https://github.com/user-attachments/assets/ec5f894f-8a4e-4a68-be0d-629d0fc31d46)

Следующим шагом нужно будет установить саму команду: 
docker sudo yum install docker-ce docker-ce-cli containerd.io
![image](https://github.com/user-attachments/assets/14b16a9d-3fde-4749-a819-e4b1cb361dc5)
![image](https://github.com/user-attachments/assets/59162f62-b1dc-4d9d-a65b-809431fcf4a1)


Следующая команда дает разрешение на автозапуск докера: 
sudo systemctl enable docker --now
![image](https://github.com/user-attachments/assets/a36318fd-745d-4d45-bafd-6699879be9c8)

Задание 3
Команда: 
COMVER=$(curl -s https://api.github.com/repos/docker/compose/releases/latest | grep 'tag_name' | cut -d\" -f4)
Получает последнюю версию Docker Compose, для этого использует API GitHub для получения информации о последнем релизе и вытаскивает номер версии из JSON ответа.
![image](https://github.com/user-attachments/assets/58fc6696-980c-4d61-afaa-1f3b7d4527d3)

Группа команд:
`sudo curl -L "https://github.com/docker/compose/releases/download/$COMVER/docker-compose-$(uname -s)-$(uname -m)" -o /usr/bin/docker-compose` 
Загружает утилиту Docker Compose, определяет операционную систему (`uname -s`) и архитектуру процессора (`uname -m`),  а затем сохраняет её в `/usr/bin/docker-compose`.
![image](https://github.com/user-attachments/assets/5c23f822-cbf6-47ac-bc04-5d9ee9518802)
![image](https://github.com/user-attachments/assets/2c7f7a18-5d02-45ce-ae88-67080d3c1190)
sudo chmod +x /usr/bin/docker-compose
• Предоставление прав на выполнение файла docker-compose.
![image](https://github.com/user-attachments/assets/de734d41-ff5c-42a9-ab5c-abdd18a26c45)

Скачиваем git команду: 
sudo yum install git
![image](https://github.com/user-attachments/assets/57b6a692-7480-4990-9773-94e1011edfff)

git clone https://github.com/skl256/grafana_stack_for_docker.git
![image](https://github.com/user-attachments/assets/1cbe4e87-0793-4d44-97c4-d549a0cde7a1)

cd grafana_stack_for_docker
![image](https://github.com/user-attachments/assets/11ac5f4d-606a-41f9-bc6e-2e81365d4f55)
sudo mkdir -p /mnt/common_volume/swarm/grafana/config
![image](https://github.com/user-attachments/assets/c8f638a5-cba5-48b5-970e-181d17cc76df)
sudo mkdir -p /mnt/common_volume/grafana/{grafana-config,grafana-data,prometheus-data}
![image](https://github.com/user-attachments/assets/121e066d-ffb4-41aa-90ed-ee24cd191947)
sudo chown -R $(id -u):$(id -g) {/mnt/common_volume/swarm/grafana/config,/mnt/common_volume/grafana}
![image](https://github.com/user-attachments/assets/12d8bef7-7870-4d76-978b-fd8b898aafab)
ls /mnt/common_volume/grafana/grafana-config/grafana.ini
![image](https://github.com/user-attachments/assets/e9cf5d18-72a1-48db-ac26-07049d948533)
cp config/* /mnt/common_volume/swarm/grafana/config/
![image](https://github.com/user-attachments/assets/e255b4da-90c1-4775-ae23-65997c0cdd75)
mv`: Это стандартная утилита Unix для **перемещения** или **изменения имени** файлов и директорий.  Если указан один путь (например, `mv file.txt newfile.txt`), она **переименует** файл. Если указаны два разных пути (например, `mv file.txt /another/directory/`), она **переместит** файл.

`grafana.yaml`: Это исходный файл, который вы хотите **переименовать**. В данном случае это файл конфигурации Grafana, написанный в формате YAML.

`docker-compose.yaml`: Это **новое имя** файла, которое будет использоваться вместо старого. В данном случае это стандартное имя для файла конфигурации Docker Compose.
![image](https://github.com/user-attachments/assets/fc09988a-ebd3-4f2b-bef6-8fa242087855)
sudo docker compose up -d
sudo: Это команда выполнения действия с правами администратора (root), если текущий пользователь не добавлен в группу docker.

docker compose: Это подкоманда Docker Compose, предназначенная для управления мультиконтейнерными приложениями через файл docker-compose.yml.

up: Эта команда создает и запускает контейнеры, описанные в файле docker-compose.yml. Если контейнеры уже существуют, они просто обновляются.

-d (отключенный режим): Этот флаг указывает, что Docker Compose запускает контейнеры в фоновом режиме без отображения логов в терминале. Это удобно для длительных задач или сценариев в производственной среде.
![image](https://github.com/user-attachments/assets/99a2a2ba-b69a-4399-8e88-c82bf0bf1ebb)

Задание 4
sudo docker compose up -d
Этот с ключом -dавтоматически переводит Docker Compose в фоновый режим.
![image](https://github.com/user-attachments/assets/79b51b80-03d8-4974-ab86-f901001321f1)
sudo docker compose up -d
На этом этаже останавливаются все активные контейнеры, связанные с проектом, который описан в файле команды docker-compose.yml
![image](https://github.com/user-attachments/assets/9613393f-5e14-41fd-a350-b66765f44bac)
sudo docker compose down
Для этого выполните следующие шаги:

• Приостанавливает все активные контейнеры, связанные с проектом.
• Удаляет контейнеры.
• Удаляет сети, созданные автоматически для данного проекта.
• По умолчанию не удаляются тома и образы, если они явно не указаны в параметрах.
![image](https://github.com/user-attachments/assets/e9968211-16ec-4a36-99ec-e595d0d5e8ba)
sudo docker compose ps
Эта выводит список контейнеров, которые относятся к текущему проекту, вместе с их состоянием команды и дополнительной информацией.
![image](https://github.com/user-attachments/assets/bb2b1319-a5d3-4e9b-b854-2532b1c50ed8)
git clone https://github.com/RabanFix/LarinLaba.git
![image](https://github.com/user-attachments/assets/2da2b148-effa-4933-82cc-67c254a0617b)
pwd
![image](https://github.com/user-attachments/assets/7f12059e-a639-44f0-b9ed-bfe9631ecf58)

















