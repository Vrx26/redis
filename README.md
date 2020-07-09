# Redis

## Запуск системы
1. Склонировать репозиторий при помощи:

``` git clone https://github.com/microservices-course-itmo/redis ```

2. Присвоить переменной окружения *HOST_IP* в файле .env ip адрес виртуальной машины. Этот адрес можно получить с помощью команды ```ip addr```

3. Если система запускается впервые, то необходимо добавить в исключения firewall следующие порты:
  - 6379, 6380, 6381 - основные порты master и slave серверов
  - 26379, 26380, 26381 - порты redis-sentinel

    В CentOS это можно сделать следующим способом:
    ```
    firewall-cmd --permanent --add-port=6379/tcp
    firewall-cmd --permanent --add-port=6380/tcp
    firewall-cmd --permanent --add-port=6381/tcp
    
    firewall-cmd --permanent --add-port=26379/tcp
    firewall-cmd --permanent --add-port=26380/tcp
    firewall-cmd --permanent --add-port=26381/tcp
    
    firewall-cmd --reload
    ```

4. Запустить систему с помощью docker-compose:

``` docker-compose up -d```

5. После этого 3 контейнера Redis Sentinel будут доступны в локальной сети на следующих адресах
  - <HOST_IP>:26379
  - <HOST_IP>:26380
  - <HOST_IP>:26381
  
