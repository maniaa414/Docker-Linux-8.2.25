# Savinova K-ISP-21 8.2.25 ``` Установка docker на Oracle Linux ```
1. Начинаем с установки пакета wget (утилиты командной строки Linux, используемой для загрузки файлов из интернета), используя команду ``` sudo yum install wget ```
   
![image](https://github.com/user-attachments/assets/f5a266e4-198d-4bfc-ad12-3e4c3dae1731)

2. Далее устанавливаем пакет curl(утилиты, котоаря используется для передачи данных с использованием различных сетевых протоколов), с помощью команды ``` sudo yum install curl ```
   
![image](https://github.com/user-attachments/assets/6ea4a9f9-8743-476f-bc5b-9941644ebe5b)

3. С помощью команды ``` sudo wget -P /etc/yum.repos.d/ ``` устанавливаем docker (платформа для разработки, доставки и запуска контейнеризированных приложений)

![image](https://github.com/user-attachments/assets/826c9bf0-6a7b-4098-a16c-6560a6f184f2)

4. Устанавливаем docker, используя команду sudo yum ``` install docker-ce docker-ce-cli containerd.io ```

![image](https://github.com/user-attachments/assets/3b99f2b3-db3b-4ace-8063-35bea3465781)
![image](https://github.com/user-attachments/assets/a565ba48-96f7-4ee5-9d63-e31a6622648a)

5. С помощью ``` sudo systemctl enable docker --now ```запускаем docker и разрешаем автозапуск.

![image](https://github.com/user-attachments/assets/978f74c7-b98e-4f31-8a6d-5613cb703c32)
