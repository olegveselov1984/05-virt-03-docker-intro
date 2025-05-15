Задание 1
https://hub.docker.com/r/olegveselov1984/custom-nginx/tags

Задание 2
![изображение](https://github.com/user-attachments/assets/11aafa59-79df-496e-820a-714fefae497b)

root@oleg-virtual-machine:/src# docker ps -a
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
root@oleg-virtual-machine:/src# sudo docker run -d -p 8080:80 --name Veselov-custom-nginx-t2 -d custom-nginx:1.0.0
74ecfdd9c7cc5b7b730ae609ab9c9b4ce4f3c1e423036c1bedd4ff677e0b2728
root@oleg-virtual-machine:/src# docker ps -a
CONTAINER ID   IMAGE                COMMAND                  CREATED          STATUS          PORTS                                     NAMES
74ecfdd9c7cc   custom-nginx:1.0.0   "/docker-entrypoint.…"   11 seconds ago   Up 11 seconds   0.0.0.0:8080->80/tcp, [::]:8080->80/tcp   Veselov-custom-nginx-t2
root@oleg-virtual-machine:/src# sudo docker rename Veselov-custom-nginx-t2 custom-nginx-t2
root@oleg-virtual-machine:/src# docker ps -a
CONTAINER ID   IMAGE                COMMAND                  CREATED          STATUS          PORTS                                     NAMES
74ecfdd9c7cc   custom-nginx:1.0.0   "/docker-entrypoint.…"   23 seconds ago   Up 23 seconds   0.0.0.0:8080->80/tcp, [::]:8080->80/tcp   custom-nginx-t2
root@oleg-virtual-machine:/src# date +"%d-%m-%Y %T.%N %Z" ; sleep 0.150 ; docker ps ; ss -tlpn | grep 127.0.0.1:8080  ; docker logs custom-nginx-t2 -n1 ; docker exec -it custom-nginx-t2 base64 /usr/share/nginx/html/index.html
14-05-2025 05:58:07.003865713 PDT
CONTAINER ID   IMAGE                COMMAND                  CREATED          STATUS          PORTS                                     NAMES
74ecfdd9c7cc   custom-nginx:1.0.0   "/docker-entrypoint.…"   48 seconds ago   Up 47 seconds   0.0.0.0:8080->80/tcp, [::]:8080->80/tcp   custom-nginx-t2
2025/05/14 12:57:19 [notice] 1#1: start worker process 30
PGh0bWw+CjxoZWFkPgpIZXksIE5ldG9sb2d5CjwvaGVhZD4KPGJvZHk+CjxoMT5JIHdpbGwgYmUg
RGV2T3BzIEVuZ2luZWVyITwvaDE+CjwvYm9keT4KPC9odG1sPgo=
root@oleg-virtual-machine:/src# curl http://127.0.0.1:8080
<html>
<head>
Hey, Netology
</head>
<body>
<h1>I will be DevOps Engineer!</h1>
</body>
</html>
root@oleg-virtual-machine:/src#

Задание 3
![изображение](https://github.com/user-attachments/assets/b0202811-da4f-41c2-ba54-5fe4d6c53684)
![изображение](https://github.com/user-attachments/assets/42a067b6-2277-43f1-b009-4f5e76aacb8b)
![изображение](https://github.com/user-attachments/assets/5fbe298a-e730-4038-bce6-5dbd75e8615e)

sudo docker attach 74ecfdd9c7cc Мы подключились в контейнер и "достали его из фона"
Ctrl-C Мы отменили работу контейнера
sudo docker ps -a 
sudo docker restart 74ecfdd9c7cc
sudo docker ps -a
sudo docker exec -it 74ecfdd9c7cc /bin/bash
apt-get update 
apt-get install nano 
nano /etc/nginx/conf.d/default.conf    80-81
nginx -s reload
exit
sudo ss -tlpn | grep 127.0.0.1:8080
sudo docker port custom-nginx-t2
sudo curl http://127.0.0.1:8080
Снаружи мы идем на порт 8080 который проброшен внутрь на порт 80, а там мы его заменили на 81. Поэтому сайт снаружи не доступен.
sudo docker rm 74ecfdd9c7cc -f

Задание 4

![изображение](https://github.com/user-attachments/assets/4bbd5c30-b30e-411b-ac17-4a94c3d330a1)
Задание 5



