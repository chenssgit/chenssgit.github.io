# 在aws amzn2 ec2上建wordpress

## 安装lamp. 基于amzn2 linux建个ec2. 登录

    sudo amazon-linux-extras install -y lamp-mariadb10.2-php7.2 php7.2   *从amzn2 extras安装php*
    sudo yum install -y httpd mariadb-server *yum安装httpd, mysql*
    sudo systemctl start httpd #启动webserver
    
访问你的$ip/已经可以看到httpd test page.   
添加'''echo "<?php phpinfo(); ?>" | sudo tee /var/www/html/phpinfo.php'''，访问$ip/phpinfo.php，可以看到php info page.

## 安装wordpress

    wget https://wordpress.org/latest.tar.gz
    sudo tar xf latest.tar.gz -C /var/www/html/
    
    # 在mysql里给wordpress建db, user
    sudo systemctl start mariadb
    mysql -u root -p
    create user $user@'localhost' identified by $yourPassword;
    create database wpdb;
    grant all privileges on wpdb.* to $user@localhost;
    flush privileges;
    exit
    
    #把dbname, dbuser, dbpassword配到wordpress配置文件中
    cd /var/www/html/wordpress
    sudo cp wp-config-sample.php wp-config.php
    # 把dbname, dbusername, password设到wp-config.php配置文件中。
    
访问$ip/wordpress，按install页面提示，一秒安装。完成。
