# docker / markdown / [It's Link](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#headers)
# how to learn and setup docker

## SETUP
1. Download docker for window 
+ [link download docker](https://docs.docker.com/docker-for-windows/install/).
2. Laradock 
+ [laradock documents](https://laradock.io/).
+ [clone project laravel for PC](git clone https://github.com/Laradock/laradock.git env).
=> tải về máy với tên thư mục là env
- run your container: **docker-compose up -d nginx mysql**
***
## configuration .env
+ app_code_path_host: //d/pj/code : trỏ đến thư mục chứa code
+ app_code_path_container: /var/www
+ app_path_host: //d/pj/data : trỏ đến data
***
### muốn thêm 1 dự án mới
- thêm 1 địa chỉ mới trong hosts
- thêm đường dẫn mới vòa .env
- copy file trong nginx/sites/xxx.conf va 
   server_name blog.local;
    root /var/www/blog/public; theo project cua minh
- k dc thi compose update sau do php artisan key:generate
- nếu thêm database đầu tiên thì chỉ cần thêm createdb.sql, còn chạy 2 pj thì cần thêm tay trong heidisql (hoặc công cụ khác)
CREATE DATABASE IF NOT EXISTS `blog` COLLATE 'utf8_general_ci' ;
GRANT ALL ON `blog`.* TO 'user'@'%' ;  => blog: tên database, user: user
- env của dự án chỉ kết nối đến database còn khi khởi tạo docker thì cần tạo database luôn
- thiết lập xong thì  chạy lênh **docker-compose up -d nginx mysql**
***
#### những lệnh docker cơ bản 
***docker-compose stop : dừng lại.
***docker-compose start: bắt đầu.
***docker-compose restart: khởi động lại.

**docker-compose down** : sẽ xóa tất cả các container trước đi, khi đã chạy lênh down ta cần chạy lệnh **docker-compose up -d nginx mysql** để tải lại các container
***

### config file env laravel
**DB_CONNECTION=mysql
DB_HOST=laradock_mysql_1**
***
### config file env của docker

- APP_CODE_PATH_HOST=//d/pj/code : trỏ đến thư mục chưa code
- APP_CODE_PATH_CONTAINER=/var/www
- DATA_PATH_HOST=//d/pj/data : trỏ đến thư mục chứa database
- COMPOSE_PATH_SEPARATOR=;
###Tìm từ khóa: Nginx và Mysql 
- MYSQL_VERSION=latest
- MYSQL_DATABASE=default
- MYSQL_USER=user
- MYSQL_PASSWORD=secret
- MYSQL_PORT=3306
- MYSQL_ROOT_PASSWORD=root

***
Truy cập theo đường dẫn ../nginx/sites/laravel.conf
copy **laravel.conf.example** và đổi tên file thành **laravel.conf**
***
***mysql
**CREATE DATABASE IF NOT EXISTS `dev_db_1` COLLATE 'utf8_general_ci' ;
#GRANT ALL ON `dev_db_1`.* TO 'user'@'%' ;
- hostname:laradock_mysql_1 (env)
- user: user
- password: secret
- post: 3306 **


- server_name sekisho.local;
    root /var/www/sekisho-jobfair/public; trong đó sekisho.local: url của pj và sekisho-jobfair: folder chứa pj laravel
