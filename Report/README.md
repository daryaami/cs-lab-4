# Лабораторная работа №4

## Ход выполнения

Для начала создаем образ контейнера для Докера.

**Содержание Dockerfile:**  
FROM ubuntu:latest  
ENV TERM xterm  
RUN apt-get update && apt-get install -y aalib-bin iputils-ping  
CMD ["aafire"]  

Делаем build образа с помощью команды `docker build -t my_image . `  

![Скриншот 1](/screenshots/Screenshot_1.png)  


Образ успешно создан и отображается в наших образах.

![Скриншот 2](/screenshots/Screenshot_2.png)


Затем запускаем контейнер из образа в интерактивном режиме командой `docker run -it my_image`:  

![Скриншот 3](/screenshots/Screenshot_3.png)  


Контейнер работает  

![Скриншот 4](/screenshots/Screenshot_4.png)


Останавливаем контейнер по его имени командой `docker stop modest_volhard`

![Скриншот 5](/screenshots/Screenshot_5.png)


Теперь из того же образа запускаем еще два контейнера в фоновом режиме. Команда `docker run -d my_image`

![Скриншот 6](/screenshots/Screenshot_6.png)


Создаем новую сеть командой `docker network create my_network`

![Скриншот 7](/screenshots/Screenshot_7.png)  


Подключаем оба контейнера к сети:

![Скриншот 8](/screenshots/Screenshot_8.png)  


С помощью команды `docker network inspect` проверяем, как работает сеть, ее настройки:

![Скриншот 9](/screenshots/Screenshot_9.png)  


Запускаем командную строку в контейнере frosty_ritchie командой `docker exec -it frosty_ritchie bash` и используем ping modest_volhard, чтобы проверить соединение между контейнерами. Соединение между контейнерами работает

![Скриншот 10](/screenshots/Screenshot_10.png)  
