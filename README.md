# Savinova K-ISP-21 8.2.25 ``` Установка docker на Oracle Linux ```
1. Начинаем с установки пакета wget (утилиты командной строки Linux, используемой для загрузки файлов из интернета), используя команду ``` sudo yum install wget ```
   
![image](https://github.com/user-attachments/assets/f5a266e4-198d-4bfc-ad12-3e4c3dae1731)

2. Далее устанавливаем пакет curl(утилиты, котоаря используется для передачи данных с использованием различных сетевых протоколов), с помощью команды ``` sudo yum install curl ```
   
![image](https://github.com/user-attachments/assets/6ea4a9f9-8743-476f-bc5b-9941644ebe5b)

3. С помощью команды ``` sudo wget -P /etc/yum.repos.d/ ``` устанавливаем docker (платформа для разработки, доставки и запуска контейнеризированных приложений)

![image](https://github.com/user-attachments/assets/826c9bf0-6a7b-4098-a16c-6560a6f184f2)

4. Устанавливаем docker, используя команду  ``` sudo yum install docker-ce docker-ce-cli containerd.io ```

![image](https://github.com/user-attachments/assets/3b99f2b3-db3b-4ace-8063-35bea3465781)
![image](https://github.com/user-attachments/assets/a565ba48-96f7-4ee5-9d63-e31a6622648a)

5. С помощью ``` sudo systemctl enable docker --now ```запускаем docker и разрешаем автозапуск.

![image](https://github.com/user-attachments/assets/978f74c7-b98e-4f31-8a6d-5613cb703c32)

# ***15.02.25 - продолжение работы c Docker***

6. С помощью команды ``` COMVER=$(curl -s https://api.github.com/repos/docker/compose/releases/latest | grep 'tag_name' | cut -d\" -f4) ``` получаем последнюю версию docker с помощью api github. ``` curl -s ``` выполняет http запрос к api для получения информации о последнем релизе репозитория docker.

![image](https://github.com/user-attachments/assets/b7b31ad6-be0e-47ed-a307-0e99c2a3100b)

7. Используя команду ``` sudo curl -L "https://github.com/docker/compose/releases/download/$COMVER/docker-compose-$(uname -s)-$(uname -m)" -o /usr/bin/docker-compose ``` загружаем и устанавливаем последнюю версию docker. Загрузка выполнена успешно.

![image](https://github.com/user-attachments/assets/7059a51f-525d-4230-9ef3-a8b13c5f592b)

8. Вводим команду ``` sudo chmod +x /usr/bin/docker-compose ``` для того, чтобы файл docker-compose стал исполняемым. ``` chmod ``` используется для изменения прав доступа к файлам и директориям.

![image](https://github.com/user-attachments/assets/a66d55f5-b7ce-465e-b6f4-f9d359a14f4c)

После делаем проверку с помощью ``` ls -l /usr/bin/docker-compose ``` и видим, что файл стал исполняемым. ``` -rwxr-xr-x``` указывает, что файл имеет права на чтение, запись и исполнение для владельца, и права на чтение и исполнение для группы и других пользователей.

![image](https://github.com/user-attachments/assets/c2d7aeff-509d-438b-8b4f-6e6e483c3e48)

9. Командой ```docker-compose --version ``` смотрим, какая версия docker у нас установлена.

![image](https://github.com/user-attachments/assets/15a60e16-9c15-4e72-9558-db442e540328)

10. 

