# docker
## Build Image
```
docker build --tag zxk114/mysql -f mysql/Dockerfile .
docker build --tag zxk114/php7 -f php7/Dockerfile .
docker build --tag zxk114/nginx -f nginx/Dockerfile .
```
## Run Container
```
docker run --name mysql -p 3306:3306 -v /root/bo/data/mysql:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=123456 -it zxk114/mysql
docker run --name php7 -p 9000:9000 -v /var/www/html:/usr/local/nginx/html --link mysql:mysql -it zxk114/php7
docker run --name nginx -p 80:80 -v /var/www/html:/usr/local/nginx/html --link php7:php7 -it zxk114/nginx
```
