# Savinova K-ISP-21 

# ***Установка docker на Oracle Linux*** *8.2.25*

1. Начинаем с установки пакета wget (утилиты командной строки Linux, используемой для загрузки файлов из интернета), используя команду

 - `sudo yum install wget`

![image](https://github.com/user-attachments/assets/f5a266e4-198d-4bfc-ad12-3e4c3dae1731)

2. Далее устанавливаем пакет curl (утилиты, котоаря используется для передачи данных с использованием различных сетевых протоколов), с помощью команды

- ``` sudo yum install curl ```
   
![image](https://github.com/user-attachments/assets/6ea4a9f9-8743-476f-bc5b-9941644ebe5b)

3. С помощью команды

- ``` sudo wget -P /etc/yum.repos.d/ ```

устанавливаем docker (платформа для разработки, доставки и запуска контейнеризированных приложений)

![image](https://github.com/user-attachments/assets/826c9bf0-6a7b-4098-a16c-6560a6f184f2)

4. Устанавливаем docker, используя команду

- ``` sudo yum install docker-ce docker-ce-cli containerd.io ```

![image](https://github.com/user-attachments/assets/3b99f2b3-db3b-4ace-8063-35bea3465781)
![image](https://github.com/user-attachments/assets/a565ba48-96f7-4ee5-9d63-e31a6622648a)

5. С помощью
   
- ``` sudo systemctl enable docker --now ```

запускаем docker и разрешаем автозапуск.

![image](https://github.com/user-attachments/assets/978f74c7-b98e-4f31-8a6d-5613cb703c32)

# ***15.02.25 - продолжение работы c Docker***

6. С помощью команды
   
- ``` COMVER=$(curl -s https://api.github.com/repos/docker/compose/releases/latest | grep 'tag_name' | cut -d\" -f4) ```

получаем последнюю версию docker с помощью api github.

- ``` curl -s ```

выполняет http запрос к api для получения информации о последнем релизе репозитория docker.

![image](https://github.com/user-attachments/assets/b7b31ad6-be0e-47ed-a307-0e99c2a3100b)

7. Используя команду
   
- ``` sudo curl -L "https://github.com/docker/compose/releases/download/$COMVER/docker-compose-$(uname -s)-$(uname -m)" -o /usr/bin/docker-compose ```

загружаем и устанавливаем последнюю версию docker. Загрузка выполнена успешно.

![image](https://github.com/user-attachments/assets/7059a51f-525d-4230-9ef3-a8b13c5f592b)

8. Вводим команду

- ``` sudo chmod +x /usr/bin/docker-compose ```

для того, чтобы файл docker-compose стал исполняемым.
- ``` chmod ```
используется для изменения прав доступа к файлам и директориям.

![image](https://github.com/user-attachments/assets/a66d55f5-b7ce-465e-b6f4-f9d359a14f4c)

После делаем проверку с помощью

- ``` ls -l /usr/bin/docker-compose ``` и видим, что файл стал исполняемым.

- ``` -rwxr-xr-x``` указывает, что файл имеет права на чтение, запись и исполнение для владельца, и права на чтение и исполнение для группы и других пользователей.

![image](https://github.com/user-attachments/assets/c2d7aeff-509d-438b-8b4f-6e6e483c3e48)

9. Командой

- ```docker-compose --version ``` смотрим, какая версия docker у нас установлена.

![image](https://github.com/user-attachments/assets/15a60e16-9c15-4e72-9558-db442e540328)

10. С помощью команды

- ``` git clone https://github.com/skl256/grafana_stack_for_docker.git ```

выполняем клонирование удаленного репозитория git, расположенного по указанному url.

![image](https://github.com/user-attachments/assets/704db6ec-a705-4339-8b13-71de3bfed61a)

11. ``` cd grafana_stack_for_docker ``` используется для смены текущей директории на указанную папку. В данном случае она переходит в директорию с именем grafana_stack_for_docker.

![image](https://github.com/user-attachments/assets/3f158e04-e77f-4263-908c-ba9fc3129cca)

12. ```sudo mkdir -p /mnt/common_volume/swarm/grafana/config``` выполняет создание директории (папки) с указанным путем, создаёт полный путь, включая все необходимые промежуточные каталоги, если они ещё не существуют.

![image](https://github.com/user-attachments/assets/d081e98c-9f08-464e-98ae-0bb180906404)

13. ```sudo mkdir -p /mnt/common_volume/grafana/{grafana-config,grafana-data,prometheus-data}``` создает несколько директорий (папок) внутри указанного пути.

![image](https://github.com/user-attachments/assets/cdaabf6e-1cec-41d9-a18c-daaf522c7e1e)

14. ``` sudo chown -R $(id -u):$(id -g) {/mnt/common_volume/swarm/grafana/config,/mnt/common_volume/grafana} ``` все файлы и каталоги в указанных директориях будут переданы в собственность текущему пользователю и его группе.

![image](https://github.com/user-attachments/assets/1bb4c071-a037-4bbe-b950-b9f6b615ac89)

15. ```touch /mnt/common_volume/grafana/grafana-config/grafana.ini``` файл grafana.ini уже существует, команда обновит его временные метки (время последнего доступа и изменения). Если файл не существует, команда создаст новый пустой файл с указанным именем по указанному пути.

![image](https://github.com/user-attachments/assets/8af235f9-2490-4305-9cc4-ca0776e78f33)

16. ```cp config/* /mnt/common_volume/swarm/grafana/config/ ``` команда копирует все файлы и подкаталоги из директории config в директорию /mnt/common_volume/swarm/grafana/config/.

![image](https://github.com/user-attachments/assets/8bf87f67-842c-49df-9554-05ed6d6f471c)

17. ``` mv grafana.yaml docker-compose.yaml ``` команда переименовывает файл grafana.yaml в docker-compose.yaml. Ничего не покажет, но можно проверить при помощи команды ls.

![image](https://github.com/user-attachments/assets/117ac187-6983-42df-b5e7-2ec3954603fb)

18. ```sudo docker compose up -d``` команда создает и запускает контейнеры в фоновом режиме, используя конфигурацию из файла docker-compose.yaml, с правами суперпользователя.

![image](https://github.com/user-attachments/assets/59331e3e-2b28-4a28-bd64-0da33c017b28)

19. ``` sudo vi docker-compose.yaml``` команда открывает файл docker-compose.yaml в текстовом редакторе vi с правами суперпользователя, что позволяет редактировать его содержимое. 

![image](https://github.com/user-attachments/assets/d71ccbab-5abc-4e41-8909-4b9c2e72b5e4)

20. `sudo docker compose up -d` создает и запускает контейнеры в фоновом режиме, если они не запущены.

![image](https://github.com/user-attachments/assets/bc158efa-1391-41e6-b91b-a104baf53443)

21. `sudo docker compose stop` останавливает запущенные контейнеры без их удаления.

![image](https://github.com/user-attachments/assets/6e2f71cf-24c1-4977-a45c-01e2dbdda23d)

22. ` sudo docker compose down ` используется для остановки и удаления контейнеров, сетей, томов и других ресурсов, созданных с помощью Docker Compose.

![image](https://github.com/user-attachments/assets/d42f8693-ed9a-4b10-875a-9bfd51e2493d)

**Работа с репозиторием и его файлами.**

- `sudo git clone https://github.com/maniaa414/Docker-Linux-8.2.25.git` клонирование репозитория Docker-Linux-8.2.25 с GitHub.

![image](https://github.com/user-attachments/assets/2274d094-eeba-4e65-b1d5-dfa3231a6668)

- `cd Docker-Linux-8.2.25`  `ls` переход в каталог Docker-Linux-8.2.25 и просмотр файлов.

- `sudo rm README.md` Открытие файла README.md с правами sudo.

![image](https://github.com/user-attachments/assets/f124e561-3f77-45e0-b048-faa085186d4e)

- `cd folder`  `ls` переход в подкаталог folder и просмотр его содержимого.
  
- `pwd` вывод полного пути текущего каталога

![image](https://github.com/user-attachments/assets/183fe980-6521-445d-b209-40475d6d0b54)


- `cp /home/savinova/Docker-Linux-8.2.25/folder/* /home/savinova/grafana_stack_for_docker` копирование всех файлов из <kbd>/home/savinova/Docker-Linux-8.2.25/folder/</kbd>(prometeus.yaml, docker-compose.yaml(изменяем основной файл в файл с Github)) в <kbd>/home/savinova/grafana_stack_for_docker</kbd>

![image](https://github.com/user-attachments/assets/93eaf503-2ee0-42eb-b4f7-3657aa1c6ef1)

- `cp prometheus.yaml prometheus.yaml1` создает копию файла prometheus.yaml с именем prometheus.yaml1. Это полезно, если нужно сохранить резервную копию конфигурации или работать с измененной версией файла, не затрагивая оригинал.
  
![image](https://github.com/user-attachments/assets/6f547fdb-a265-4379-9871-86c9e4e325b4)

- `sudo cp prometheus.yaml /mnt/common_volume/swarm/grafana/config` выполняет копирование файла **prometheus.yaml** в указанную директорию с использованием прав администратора (sudo).

![image](https://github.com/user-attachments/assets/51fcc89c-fd16-4583-8b33-8f0e808ae289)

- `ls` команда выводит список файлов в директории.

![image](https://github.com/user-attachments/assets/a2ba60f2-6492-45cd-9d1b-978769de4cee)

# ***Grafana***

- Переходим на сайт **localhost:3000**. - Пользователь и пароль: admin. - Код графаны 1816. - Код прометеуса: http://prometheus:9090.

![image](https://github.com/user-attachments/assets/6e2e1a9b-4261-4db7-8a0e-19d62c5631e5)

- Интерфейс графаны.

![image](https://github.com/user-attachments/assets/7eb6a34e-c244-4a5b-96e9-69cdf5627c6c)

- Переход в  **dashboars** и создание нового борда.

![image](https://github.com/user-attachments/assets/e851eec3-7e40-42f9-b1d4-5681cd956439)

- Создание визуализации.
  
![image](https://github.com/user-attachments/assets/dad3386a-3da5-4519-9792-af080bbd4ab2)

- Выбираю `prometheus`
  
![image](https://github.com/user-attachments/assets/4c1957da-3be1-4b5a-a614-c5c1b93f9dd4)

- Ставлю аутентификацию и url `prometheus`.

![image](https://github.com/user-attachments/assets/df5d06e3-09a6-44b2-904b-744cb9067c11)

- Сохраняю и проверяю, что все супер.

![image](https://github.com/user-attachments/assets/b71785da-8198-4541-8497-fa5096fb7065)

- Импорт 1860 dashboard.

![image](https://github.com/user-attachments/assets/6fa770d9-acb0-4dc8-afc3-51d60e9d6aa5)

- Выбираю prometheus и импортирую.

![image](https://github.com/user-attachments/assets/0ca8d7a8-50e3-4030-939f-4e06782b3f0d)

- Результат мониторинга.

![image](https://github.com/user-attachments/assets/03ef6038-65a2-4ae0-9975-6830b04f4884)





 




