

Установка новой виртуальной машины

Разворачиваю новую виртуальную машину с такой же конфигурацией, как и предыдущая

Первым делом устанавливаю необходимые утилиты одной командой: `sudo yum install` сразу wget curl и git

Это позволяет сразу получить инструменты для загрузки файлов (wget, curl) и работы с репозиториями (git)

![image](https://github.com/user-attachments/assets/c927d66a-4c58-40c2-9d17-a998e852613e)

Проверка состояния firewall

Выполняю команду для проверки состояния межсетевого экрана:
`sudo firewall-cmd --state`

![image](https://github.com/user-attachments/assets/d3aa9a44-1b47-4649-8788-eb599c03af10)

Установка архиватора tar

Устанавливаю утилиту для работы с архивами:

`sudo yum install wget tar`

![image](https://github.com/user-attachments/assets/dabc8e1b-9f27-4599-ac56-bb3e6ecc682a)

становка и настройка chrony (сервис синхронизации времени)

Устанавливаю пакет chrony:

`sudo yum install chrony`
![image](https://github.com/user-attachments/assets/2c2e6f0e-5898-4a5c-9c56-1060ab77f723)

Настраиваю автозапуск chrony при загрузке системы:

`systemctl enable chronyd`

Запускаю службу немедленно:

`systemctl start chronyd`

![image](https://github.com/user-attachments/assets/26216333-d69b-4235-ab30-53b3e5120be3)

Работа с SELinux

Проверяю текущий режим SELinux командой:

`getenforce`

Получаю ответ "Enforcing", что означает активную защиту

Временно перевожу SELinux в разрешающий режим:

`sudo setenforce 0`

На постоянной основе отключаю SELinux через конфигурационный файл:
`sudo sed -i 's/^SELINUX=.*/SELINUX=disabled/g' /etc/selinux/config`

![image](https://github.com/user-attachments/assets/84d357e7-4bc4-425c-a34f-5b937281fdfb)

Установка Prometheus

Скачиваю архив с Prometheus (версия для Linux amd64)

![image](https://github.com/user-attachments/assets/11a3fcaf-143f-4ae3-9345-bafe1c8e1c91)

Создаю необходимые директории для работы Prometheus:

`sudo mkdir -p /etc/prometheus /var/lib/prometheus`

![image](https://github.com/user-attachments/assets/6549c079-4da4-4256-80d8-02545087ae07)

Распаковываю скачанный архив:

`tar -zxf prometheus-*.linux-amd64.tar.gz`

Перехожу в распакованную директорию:

`cd prometheus-*.linux-amd64`


![image](https://github.com/user-attachments/assets/a32513a4-297e-4388-b277-a0c76c6022ff)

Проверяю с помощью pwd корректность папки

![image](https://github.com/user-attachments/assets/0fa452d6-a928-4940-bddc-add3fc0152e3)

Скопировала файлы Prometheus в системные директории:

`sudo cp prometheus promtool /usr/local/bin/`
`sudo cp prometheus.yml /etc/prometheus/`

![image](https://github.com/user-attachments/assets/2e5794e2-5f95-4736-b4d9-6cc30caa38bf)

Очистка временных файлов командой и повторная команда pwd:

`cd .. && rm -rf prometheus-*.linux-amd64/ && rm -f prometheus-*.linux-amd64.tar.gz`

Возвращаюсь на уровень выше в директории:

cd ..
Удаляю распакованную директорию Prometheus:

rm -rf prometheus-*.linux-amd64/
Удаляю архивный файл:

rm -f prometheus-*.linux-amd64.tar.gz
Повторно проверяю текущую директорию командой pwd

![image](https://github.com/user-attachments/assets/adeea23c-f459-4702-aa22-6fa8b8e1b27a)

Проверяю содержимое директории с помощью ls -l
![image](https://github.com/user-attachments/assets/41593a5f-6ab3-4a51-ad9a-ba38a1159f0f)



