## 安装步骤

### 配置PHP mcrypt.so

1. brew install mcrypt
2. 到 PHP 官网下载对应的 PHP 版本
3. tar -xvrf php-zip-file 
4. cd php-zip-file/ext/mcrypt
5. phpize
6. ./configure
7. make
8. sudo make install
9. 如果出现 permission 错误, 可直接找到编译好的 mcrypt.so 文件 复制到 /usr/local/bin/php/extensions/
9. vim /etc/php.ini, 添加 extension=mcrypt.so , extension_dir=/usr/local/bin/php/extensions/
10. composer install


### migrate 
1. 修改数据库配置, localhost 改为 127.0.0.1 
2. mysql 创建 phphub 数据库
3. php artisan migrate (原版本会因为, timestamps字段报错, 改为 nullableTimestamps 就work)
4. php artisan db:seed 初始化测试数据, 原版本会有一些字段没有默认值报错, 已修改


### 前端
1. npm install (gulp-sass 原版本安装会报错, 已修改)
2. sudo npm install gulp -g


### 启动服务
1. php -S localhost:8888 -t public  