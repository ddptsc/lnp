
#######通过docker-compose生成
docker-compose -f lnmp.yml up -d


########手动生成
进入dockerfile文件夹可手动构建镜像容器
cd dockerfile

生成php容器
docker run -d --name phpto -p 9001:9000 -v E:/lnmp/www:/usr/local/nginx/html/ -it lnmp/php
生成nginx容器
docker run -d --name nginxto -d -p 8002:80 -v E:/lnmp/www:/usr/local/nginx/html/ -v E:/lnmp/config/nginx.conf:/usr/local/nginx/conf/nginx.conf --link phpto:php -it lnmp/nginxto

构建php镜像
docker build --tag lnmp/phpto -f nginx-dockerfile .
构建nginx镜像
docker build --tag lnmp/phpto -f phpto-dockerfile .

进入php容器
docker exec -it php /bin/bash


