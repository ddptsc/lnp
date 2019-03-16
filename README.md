
#######通过docker-compose生成  
docker-compose -f lnmp.yml up -d  


########手动生成  
进入dockerfile文件夹可手动构建镜像容器  
cd dockerfile  

生成php容器  
docker run -d --name lnmp_php -p 9002:9000 -v ./www:/usr/local/nginx/html/ -itd lnmp_lnmp_php
生成nginx容器  
docker run -d --name lnmp_nginx -d -p 8002:80 -v ./www:/usr/local/nginx/html/ -v ./config/nginx.conf:/usr/local/nginx/conf/nginx.conf --link lnmp_php:php -itd lnmp_lnmp_nginx  

构建php镜像  
docker build --tag lnmp/php -f nginx-dockerfile .  
构建nginx镜像  
docker build --tag lnmp/php -f phpto-dockerfile .  

进入php容器  
docker exec -it lnmp_php /bin/bash  

 *****************************************************************  
 
#######docker-compose镜像生成  
docker-compose -f lnmp.yml up -d  


