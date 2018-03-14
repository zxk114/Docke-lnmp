# docker
## Build Image
```
docker build --tag addcn/mysql -f mysql/Dockerfile .
docker build --tag addcn/php7 -f php7/Dockerfile .
docker build --tag addcn/nginx -f nginx/Dockerfile .
```
## Run Container
```
docker run --name mysql -p 3306:3306 -v /root/bo/data/mysql:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=123456 -it addcn/mysql
docker run --name php7 -p 9000:9000 -v /var/www/html:/usr/local/nginx/html --link mysql:mysql -it addcn/php7
docker run --name nginx -p 80:80 -v /var/www/html:/usr/local/nginx/html --link php7:php7 -it addcn/nginx
```
