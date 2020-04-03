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
### muốn thêm 1 dự án mới
- thêm 1 địa chỉ mới trong hosts
- thêm đường dẫn mới vòa .env

thiết lập xong thì  chạy lênh
