## Linux安装MySQL

#### 安装MySQL:  
          sudo apt install mysql-server

#### 进入MySQL:
          mysql -uroot -p1
          -u是用户
          -p后面是密码

          或
          mysql -uroot -p
          Enter password :这里输入密码

#### 查看环境配置:
        Linux下,有些编码默认是latin1,要将其修改为utf8才能真正适合项目需求,不然会报错
        --查看编码集
        mysql> show variables like '%char%';
        show:显示   VARIABLES:变量   LIKE:环境匹配

        --查看校对集
        mysql> show variables like '%colla%';

#### 停止mysql服务器:
               sudo service mysql stop

#### 查看mysql服务状态:
               sudo service mysql startus

#### 修改环境配置:
         MySQL的配置环境是/etc/mysql/my.cnf
         cd /etc/mysql
         sudo nano my.cnf
         配置文件最下方,添加:
         [client]
         default-character-set = utf8

         [mysqld]
         character-set-server = utf8
         collation-server = utf8_general_ci
         bind-address = 0.0.0.0          #任何一台计算机都可以访问

         (或bind-address = localhost        #只有本机可以访问)
         重启MySQL服务,可能会失败,启动两次

#### 查看修改是否成功:
     启动mysql服务器:
                   sudo service mysql start
     进入mysql:                 
                   mysql -uroot -p
