Яхункин К-ИСП 39-1 
Лабораторная работа



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

скачиваем скрипт 
`sudo curl -L "https://github.com/docker/compose/releases/download/$COMVER/docker-compose-$(uname -s)-$(uname -m)" -o /usr/bin/docker-compose`
![image](https://github.com/user-attachments/assets/facf9656-2d25-4fce-ab52-ce5bb666b556)

предоставляем права на выполнение Docker Compose
`sudo chmod +x /usr/bin/docker-compose`
![image](https://github.com/user-attachments/assets/8572a382-945a-40a5-8466-d5427867ddd4)

проверяем версью Docker
![image](https://github.com/user-attachments/assets/d8941e15-b384-46b1-9031-205272b9a6fb)

скачиваем скрипт докера:
![image](https://github.com/user-attachments/assets/c7c03e41-1ee4-4845-af98-c2748b440ac7)

Даем право на выполнение:
![image](https://github.com/user-attachments/assets/3c157462-a37d-4406-b576-f28b6b25883b)

проверка версии:
![image](https://github.com/user-attachments/assets/5c8a510a-218e-42b6-8438-e07c869cda5b)

качаем гит:
![image](https://github.com/user-attachments/assets/6cfcc875-0e6d-48cd-a71a-79a78e6eab5e)

выдает ошибку, вводим другую команду:
![image](https://github.com/user-attachments/assets/c38399ce-3d0c-4b11-a588-095e50db81ea)

команда
![image](https://github.com/user-attachments/assets/dcb332bf-c8c2-4f02-ac91-47db749434ef)

при переходе в папку выдает ошибку:
![image](https://github.com/user-attachments/assets/823cbda5-2709-42d8-b63d-4fb384381a69)

проверяем все ли команды введены:
![image](https://github.com/user-attachments/assets/4c91b75d-7104-49b3-9ce9-477af5f6bf7b)

создаем путь:
![image](https://github.com/user-attachments/assets/374953f5-9b30-4951-acb9-061514150f27)

![image](https://github.com/user-attachments/assets/d1cf79aa-f24e-4310-aa92-bb93befb0900)

![image](https://github.com/user-attachments/assets/9677466b-c8f3-4000-a4d4-b4c7d0d77c2d)





































