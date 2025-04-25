

Устанавливаю новую такую же виртуальную машину. и ставлю одной командой `sudo yum install` сразу wget curl и git
![image](https://github.com/user-attachments/assets/c927d66a-4c58-40c2-9d17-a998e852613e)

Проверяю фаерволл командой
`sudo firewall-cmd --state`

![image](https://github.com/user-attachments/assets/d3aa9a44-1b47-4649-8788-eb599c03af10)

устанавливаю tar

`sudo yum install wget tar`
![image](https://github.com/user-attachments/assets/dabc8e1b-9f27-4599-ac56-bb3e6ecc682a)

Устанавливаю chrony

`sudo yum install chrony`
![image](https://github.com/user-attachments/assets/2c2e6f0e-5898-4a5c-9c56-1060ab77f723)

разрешаю запуск chony и запускаю

`systemctl enable chronyd`

`systemctl start chronyd`

![image](https://github.com/user-attachments/assets/26216333-d69b-4235-ab30-53b3e5120be3)

При вводе команды getenforce получила ответ: Enforcing. Поэтому пришлось использовать следующие команды для отключения гетинфорс:

`sudo setenforce 0`
`sudo sed -i 's/^SELINUX=.*/SELINUX=disabled/g' /etc/selinux/config`

![image](https://github.com/user-attachments/assets/84d357e7-4bc4-425c-a34f-5b937281fdfb)

Скачала прометиус

![image](https://github.com/user-attachments/assets/11a3fcaf-143f-4ae3-9345-bafe1c8e1c91)

Создаю директорию для прометиуса

`sudo mkdir -p /etc/prometheus /var/lib/prometheus`

![image](https://github.com/user-attachments/assets/6549c079-4da4-4256-80d8-02545087ae07)

Разархивировал файл командой `tar -zxf prometheus-*.linux-amd64.tar.gz` и перешёл в папку prometheus-*.linux-amd64 командой `cd prometheus-*.linux-amd64`


![image](https://github.com/user-attachments/assets/a32513a4-297e-4388-b277-a0c76c6022ff)

Проверяю с помощью pwd корректность папки

![image](https://github.com/user-attachments/assets/0fa452d6-a928-4940-bddc-add3fc0152e3)

Скопировала файлы Prometheus в системные директории:

`sudo cp prometheus promtool /usr/local/bin/`
`sudo cp prometheus.yml /etc/prometheus/`

![image](https://github.com/user-attachments/assets/2e5794e2-5f95-4736-b4d9-6cc30caa38bf)

Очистка временных файлов командой и повторная команда pwd:

`cd .. && rm -rf prometheus-*.linux-amd64/ && rm -f prometheus-*.linux-amd64.tar.gz`

![image](https://github.com/user-attachments/assets/adeea23c-f459-4702-aa22-6fa8b8e1b27a)

Проверяю содержимое директории с помощью ls -l
![image](https://github.com/user-attachments/assets/41593a5f-6ab3-4a51-ad9a-ba38a1159f0f)



