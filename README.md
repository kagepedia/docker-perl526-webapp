# Perl5.26 + Apache2 + MySQL

## Getting Started

### common setting

    $ git clone https://github.com/kagepedia/docker-perl526-webapp
    $ cd docker-perl526-webapp
    $ docker-compose build
    $ dokcer-compose up -d
    $ docker exec -it <CONTAINER_ID> /bin/bash

### apache setting

change documentroot edit `000-default.conf` and `default-ssl.conf` files  
use cgi edit `000-default.conf`

example.

    AddHandler cgi-script .cgi
    <Directory "/var/www/cgi-bin">
            AllowOverride None
            Require all granted
            Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
            Order allow,deny
            Allow from all
    </Directory>

apache2 restart

    $ service apache2 reload

[Apache2@Debian でのバーチャルホスト設定まとめ](https://qiita.com/ninneko/items/87a76f0f1dc6d82500fb)  
[ubuntu16.04 の Apache2 設定/cgi 設定](https://qiita.com/kummn/items/f6bd0f3e643595ed077a)

### mysql setting
install  

    $ mkdir ~/src
    $ cd ~/src
    $ wget http://dev.mysql.com/get/mysql-apt-config_0.8.17-1_all.deb
    $ dpkg -i mysql-apt-config_0.8.17-1_all.deb
    # 対話 1 → 1 → 4 （MySQLバージョンなど設定）
    $ apt-get update
    $ apt-get -y install mysql-server
    # 対話パスワード設定 <PASSWORD>/<PASSWORD> （設定）
    $ service mysql start

mysql login

    $ mysql -u<ACCOUNT> -p<PASSWORD>
    
    
