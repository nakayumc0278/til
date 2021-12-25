## httpdバージョンチェック

```
$ httpd -v
Server version: Apache/2.4.51 ()
Server built:   Oct  8 2021 22:03:47
```

## phpインストールチェック

```
rpm -qa | grep php 
php-common-7.2.24-1.amzn2.0.1.x86_64
php-cli-7.2.24-1.amzn2.0.1.x86_64
php-process-7.2.24-1.amzn2.0.1.x86_64
php-devel-7.2.24-1.amzn2.0.1.x86_64
php-json-7.2.24-1.amzn2.0.1.x86_64
php-pdo-7.2.24-1.amzn2.0.1.x86_64
php-fpm-7.2.24-1.amzn2.0.1.x86_64
php-pear-1.10.12-9.amzn2.noarch
php-mysqlnd-7.2.24-1.amzn2.0.1.x86_64
php-xml-7.2.24-1.amzn2.0.1.x86_64
```

## php一部ないので、serverworld基準でインストール

```
yum -y install php php-mbstring
```

## php timezone変更

```
vi /etc/php.ini

[Date]
; Defines the default timezone used by the date functions
; http://php.net/date.timezone
- ;date.timezone = 
+ date.timezone = "Asia/Tokyo"
+ 
```

## mariadb-serverがいないのでインストールし、初期化

```
$ rpm -qa | grep db 
gdb-gdbserver-8.0.1-36.amzn2.0.1.x86_64
gdbm-1.13-6.amzn2.0.2.x86_64
apr-util-bdb-1.6.1-5.amzn2.0.2.x86_64
libdb-5.3.21-24.amzn2.0.3.x86_64
mariadb-libs-10.2.38-1.amzn2.0.1.x86_64
python-pillow-2.0.0-21.gitd1c6db8.amzn2.0.1.x86_64
dbus-libs-1.10.24-7.amzn2.x86_64
dbus-1.10.24-7.amzn2.x86_64
gdb-8.0.1-36.amzn2.0.1.x86_64
mariadb-common-10.2.38-1.amzn2.0.1.x86_64
mariadb-10.2.38-1.amzn2.0.1.x86_64
libdb-utils-5.3.21-24.amzn2.0.3.x86_64
man-db-2.6.3-9.amzn2.0.3.x86_64
mariadb-config-10.2.38-1.amzn2.0.1.x86_64
```

```
$ yum -y install mariadb-server

==================================================================================================
 Package                    Arch   Version               Repository                          Size
==================================================================================================
Installing:
 mariadb-server             x86_64 3:10.2.38-1.amzn2.0.1 amzn2extra-lamp-mariadb10.2-php7.2  17 M
Installing for dependencies:
 mariadb-backup             x86_64 3:10.2.38-1.amzn2.0.1 amzn2extra-lamp-mariadb10.2-php7.2 5.9 M
 mariadb-cracklib-password-check
                            x86_64 3:10.2.38-1.amzn2.0.1 amzn2extra-lamp-mariadb10.2-php7.2  37 k
 mariadb-errmsg             x86_64 3:10.2.38-1.amzn2.0.1 amzn2extra-lamp-mariadb10.2-php7.2 222 k
 mariadb-gssapi-server      x86_64 3:10.2.38-1.amzn2.0.1 amzn2extra-lamp-mariadb10.2-php7.2  39 k
 mariadb-rocksdb-engine     x86_64 3:10.2.38-1.amzn2.0.1 amzn2extra-lamp-mariadb10.2-php7.2 5.5 M
 mariadb-server-utils       x86_64 3:10.2.38-1.amzn2.0.1 amzn2extra-lamp-mariadb10.2-php7.2 1.6 M
 mariadb-tokudb-engine      x86_64 3:10.2.38-1.amzn2.0.1 amzn2extra-lamp-mariadb10.2-php7.2 833 k
 perl-Compress-Raw-Bzip2    x86_64 2.061-3.amzn2.0.2     amzn2-core                          32 k
 perl-Compress-Raw-Zlib     x86_64 1:2.061-4.amzn2.0.2   amzn2-core                          58 k
 perl-DBD-MySQL             x86_64 4.023-6.amzn2         amzn2-core                         141 k
 perl-DBI                   x86_64 1.627-4.amzn2.0.2     amzn2-core                         804 k
 perl-IO-Compress           noarch 2.061-2.amzn2         amzn2-core                         260 k
 perl-Net-Daemon            noarch 0.48-5.amzn2          amzn2-core                          51 k
 perl-PlRPC                 noarch 0.2020-14.amzn2       amzn2-core                          36 k
 
```


```
$ vi /etc/my.cnf 
 [mysqld]
# Disabling symbolic-links is recommended to prevent assorted security risks
symbolic-links=0
+ character-set-server=utf8
```

## MariaDB起動&自動起動有効

```
systemctl enable --now mariadb
```


## 初期設定

```
#  mysql_secure_installation 

NOTE: RUNNING ALL PARTS OF THIS SCRIPT IS RECOMMENDED FOR ALL MariaDB
      SERVERS IN PRODUCTION USE!  PLEASE READ EACH STEP CAREFULLY!

In order to log into MariaDB to secure it, we'll need the current
password for the root user.  If you've just installed MariaDB, and
you haven't set the root password yet, the password will be blank,
so you should just press enter here.

#現在パスワードを入力（なしなのでenter）
Enter current password for root (enter for none): 
OK, successfully used password, moving on...

Setting the root password ensures that nobody can log into the MariaDB
root user without the proper authorisation.

#rootパスワード入力(Cnetuser)
Set root password? [Y/n] y
New password: 
Re-enter new password: 
Password updated successfully!
Reloading privilege tables..
 ... Success!


By default, a MariaDB installation has an anonymous user, allowing anyone
to log into MariaDB without having to have a user account created for
them.  This is intended only for testing, and to make the installation
go a bit smoother.  You should remove them before moving into a
production environment.

# 匿名ユーザーは削除
Remove anonymous users? [Y/n] Y
 ... Success!

Normally, root should only be allowed to connect from 'localhost'.  This
ensures that someone cannot guess at the root password from the network.

# root のリモートログインは有効のままにしとく
Disallow root login remotely? [Y/n] n
 ... skipping.

By default, MariaDB comes with a database named 'test' that anyone can
access.  This is also intended only for testing, and should be removed
before moving into a production environment.

# テストデータベースは削除
Remove test database and access to it? [Y/n] y
 - Dropping test database...
 ... Success!
 - Removing privileges on test database...
 ... Success!

Reloading the privilege tables will ensure that all changes made so far
will take effect immediately.


# 特権情報リロード
Reload privilege tables now? [Y/n] y
 ... Success!

Cleaning up...

All done!  If you've completed all of the above steps, your MariaDB
installation should now be secure.

Thanks for using MariaDB!
```

## インストールできたか確認

```
$ rpm -qa | grep mariadb 
mariadb-errmsg-10.2.38-1.amzn2.0.1.x86_64
mariadb-backup-10.2.38-1.amzn2.0.1.x86_64
mariadb-libs-10.2.38-1.amzn2.0.1.x86_64
mariadb-common-10.2.38-1.amzn2.0.1.x86_64
mariadb-10.2.38-1.amzn2.0.1.x86_64
mariadb-rocksdb-engine-10.2.38-1.amzn2.0.1.x86_64
mariadb-cracklib-password-check-10.2.38-1.amzn2.0.1.x86_64
mariadb-server-utils-10.2.38-1.amzn2.0.1.x86_64
mariadb-gssapi-server-10.2.38-1.amzn2.0.1.x86_64
mariadb-tokudb-engine-10.2.38-1.amzn2.0.1.x86_64
mariadb-server-10.2.38-1.amzn2.0.1.x86_64
mariadb-config-10.2.38-1.amzn2.0.1.x86_64
```

## net-snmpの設定

```
$ vi /etc/snmp/snmpd.conf
####
# First, map the community name "public" into a "security name
#       sec.name  source          community
- com2sec notConfigUser  default       public
+ com2sec mynetwork  localhost      nakayumc
+ com2sec mynetwork  172.31.32.0/20 nakayumc

####
# Second, map the security name into a group name:

#       groupName      securityModel securityName
- group   notConfigGroup v1           notConfigUser
- group   notConfigGroup v2c           notConfigUser
+ group   mynetwork_group v1            mynetwork
+ group   mynetwork_group v2c           mynetwork

####
# Third, create a view for us to let the group have rights to:

# Make at least  snmpwalk -v 1 localhost -c public system fast again.
#       name           incl/excl     subtree         mask(optional)
view    systemview    included   .1.3.6.1.2.1.1
view    systemview    included   .1.3.6.1.2.1.25.1.1
+ view    systemview    included   .1.3.6.1.
+ view    all_view      included   .1

- access  notConfigGroup ""      any       noauth    exact  systemview none none
+ access  mynetwork_group ""      any       noauth    exact  systemview none none
+ access  mynetwork_group ""      any       noauth    exact  all_view none none

# disk PATH [MIN=100000]
#
# PATH:  mount path to the disk in question.
# MIN:   Disks with space below this value will have the Mib's errorFlag set.
#        Default value = 100000.

# Check the / partition and make sure it contains at least 10 megs.

- #disk / 10000
+ disk / 10000

```

## net-snmp 再起動

```
$ systemctl restart snmpd
$ systemctl enable snmpd
```

## snmpwalk コマンドで動作確認

```
$ snmpwalk -v 2c -c nakayumc 172.31.46.85

SNMPv2-MIB::sysDescr.0 = STRING: Linux ip-172-31-46-85.ap-northeast-1.compute.internal 4.14.256-197.484.amzn2.x86_64 #1 SMP Tue Nov 30 00:17:50 UTC 2021 x86_64
SNMPv2-MIB::sysObjectID.0 = OID: NET-SNMP-MIB::netSnmpAgentOIDs.10
DISMAN-EVENT-MIB::sysUpTimeInstance = Timeticks: (27012) 0:04:30.12
SNMPv2-MIB::sysContact.0 = STRING: Root <root@localhost> (configure /etc/snmp/snmp.local.conf)
SNMPv2-MIB::sysName.0 = STRING: ip-172-31-46-85.ap-northeast-1.compute.internal
SNMPv2-MIB::sysLocation.0 = STRING: Unknown (edit /etc/snmp/snmpd.conf)
SNMPv2-MIB::sysORLastChange.0 = Timeticks: (4) 0:00:00.04
SNMPv2-MIB::sysORID.1 = OID: SNMP-MPD-MIB::snmpMPDCompliance
SNMPv2-MIB::sysORID.2 = OID: SNMP-USER-BASED-SM-MIB::usmMIBCompliance
SNMPv2-MIB::sysORID.3 = OID: SNMP-FRAMEWORK-MIB::snmpFrameworkMIBCompliance
SNMPv2-MIB::sysORID.4 = OID: SNMPv2-MIB::snmpMIB
SNMPv2-MIB::sysORID.5 = OID: TCP-MIB::tcpMIB
SNMPv2-MIB::sysORID.6 = OID: IP-MIB::ip
SNMPv2-MIB::sysORID.7 = OID: UDP-MIB::udpMIB
SNMPv2-MIB::sysORID.8 = OID: SNMP-VIEW-BASED-ACM-MIB::vacmBasicGroup
SNMPv2-MIB::sysORID.9 = OID: SNMP-NOTIFICATION-MIB::snmpNotifyFullCompliance
SNMPv2-MIB::sysORID.10 = OID: NOTIFICATION-LOG-MIB::notificationLogMIB
SNMPv2-MIB::sysORDescr.1 = STRING: The MIB for Message Processing and Dispatching.
SNMPv2-MIB::sysORDescr.2 = STRING: The management information definitions for the SNMP User-based Security Model.
SNMPv2-MIB::sysORDescr.3 = STRING: The SNMP Management Architecture MIB.
SNMPv2-MIB::sysORDescr.4 = STRING: The MIB module for SNMPv2 entities
SNMPv2-MIB::sysORDescr.5 = STRING: The MIB module for managing TCP implementations
SNMPv2-MIB::sysORDescr.6 = STRING: The MIB module for managing IP and ICMP implementations
SNMPv2-MIB::sysORDescr.7 = STRING: The MIB module for managing UDP implementations
SNMPv2-MIB::sysORDescr.8 = STRING: View-based Access Control Model for SNMP.
SNMPv2-MIB::sysORDescr.9 = STRING: The MIB modules for managing SNMP Notification, plus filtering.
SNMPv2-MIB::sysORDescr.10 = STRING: The MIB module for logging SNMP Notifications.
SNMPv2-MIB::sysORUpTime.1 = Timeticks: (4) 0:00:00.04
SNMPv2-MIB::sysORUpTime.2 = Timeticks: (4) 0:00:00.04
SNMPv2-MIB::sysORUpTime.3 = Timeticks: (4) 0:00:00.04
SNMPv2-MIB::sysORUpTime.4 = Timeticks: (4) 0:00:00.04
SNMPv2-MIB::sysORUpTime.5 = Timeticks: (4) 0:00:00.04
SNMPv2-MIB::sysORUpTime.6 = Timeticks: (4) 0:00:00.04
SNMPv2-MIB::sysORUpTime.7 = Timeticks: (4) 0:00:00.04
SNMPv2-MIB::sysORUpTime.8 = Timeticks: (4) 0:00:00.04
SNMPv2-MIB::sysORUpTime.9 = Timeticks: (4) 0:00:00.04
SNMPv2-MIB::sysORUpTime.10 = Timeticks: (4) 0:00:00.04
HOST-RESOURCES-MIB::hrSystemUptime.0 = Timeticks: (2699433) 7:29:54.33
HOST-RESOURCES-MIB::hrSystemUptime.0 = No more variables left in this MIB View (It is pastthe end of the MIB tree)
・
・
・
```

## cacti を yum でインストールする

```
$ yum install cacti

=======================================================================================================
 Package              Arch   Version                          Repository                          Size
=======================================================================================================
Installing:
 cacti                noarch 1.2.19-1.el7                     epel                                31 M
Installing for dependencies:
 cairo                x86_64 1.15.12-4.amzn2                  amzn2-core                         732 k
 dejavu-sans-mono-fonts
                      noarch 2.33-6.amzn2                     amzn2-core                         433 k
 fribidi              x86_64 1.0.2-1.amzn2.1                  amzn2-core                          79 k
 graphite2            x86_64 1.3.10-1.amzn2.0.2               amzn2-core                         115 k
 harfbuzz             x86_64 1.7.5-2.amzn2                    amzn2-core                         279 k
 libX11               x86_64 1.6.7-3.amzn2.0.2                amzn2-core                         606 k
 libX11-common        noarch 1.6.7-3.amzn2.0.2                amzn2-core                         165 k
 libXau               x86_64 1.0.8-2.1.amzn2.0.2              amzn2-core                          29 k
 libXdamage           x86_64 1.1.4-4.1.amzn2.0.2              amzn2-core                          20 k
 libXext              x86_64 1.3.3-3.amzn2.0.2                amzn2-core                          39 k
 libXfixes            x86_64 5.0.3-1.amzn2.0.2                amzn2-core                          18 k
 libXft               x86_64 2.3.2-2.amzn2.0.2                amzn2-core                          60 k
 libXpm               x86_64 3.5.12-1.amzn2.0.2               amzn2-core                          57 k
 libXrender           x86_64 0.9.10-1.amzn2.0.2               amzn2-core                          26 k
 libXxf86vm           x86_64 1.1.4-1.amzn2.0.2                amzn2-core                          17 k
 libglvnd             x86_64 1:1.0.1-0.1.git5baa1e5.amzn2.0.1 amzn2-core                          89 k
 libglvnd-egl         x86_64 1:1.0.1-0.1.git5baa1e5.amzn2.0.1 amzn2-core                          43 k
 libglvnd-glx         x86_64 1:1.0.1-0.1.git5baa1e5.amzn2.0.1 amzn2-core                         125 k
 libthai              x86_64 0.1.14-9.amzn2.0.2               amzn2-core                         187 k
 libwayland-client    x86_64 1.17.0-1.amzn2                   amzn2-core                          34 k
 libwayland-server    x86_64 1.17.0-1.amzn2                   amzn2-core                          40 k
 libxcb               x86_64 1.12-1.amzn2.0.2                 amzn2-core                         216 k
 libxshmfence         x86_64 1.2-1.amzn2.0.2                  amzn2-core                         7.2 k
 mesa-libEGL          x86_64 18.3.4-5.amzn2.0.1               amzn2-core                         108 k
 mesa-libGL           x86_64 18.3.4-5.amzn2.0.1               amzn2-core                         162 k
 mesa-libgbm          x86_64 18.3.4-5.amzn2.0.1               amzn2-core                          38 k
 mesa-libglapi        x86_64 18.3.4-5.amzn2.0.1               amzn2-core                          45 k
 net-snmp             x86_64 1:5.7.2-49.amzn2.1               amzn2-core                         325 k
 net-snmp-agent-libs  x86_64 1:5.7.2-49.amzn2.1               amzn2-core                         701 k
 net-snmp-libs        x86_64 1:5.7.2-49.amzn2.1               amzn2-core                         748 k
 net-snmp-utils       x86_64 1:5.7.2-49.amzn2.1               amzn2-core                         200 k
 pango                x86_64 1.42.4-4.amzn2                   amzn2-core                         280 k
 php-gd               x86_64 7.2.24-1.amzn2.0.1               amzn2extra-lamp-mariadb10.2-php7.2 179 k
 php-gmp              x86_64 7.2.24-1.amzn2.0.1               amzn2extra-lamp-mariadb10.2-php7.2  75 k
 php-intl             x86_64 7.2.24-1.amzn2.0.1               amzn2extra-lamp-mariadb10.2-php7.2 223 k
 php-ldap             x86_64 7.2.24-1.amzn2.0.1               amzn2extra-lamp-mariadb10.2-php7.2  78 k
 php-snmp             x86_64 7.2.24-1.amzn2.0.1               amzn2extra-lamp-mariadb10.2-php7.2  72 k
 pixman               x86_64 0.34.0-1.amzn2.0.2               amzn2-core                         254 k
 rrdtool              x86_64 1.4.8-9.amzn2.0.1                amzn2-core                         369 k
```

## cacti ユーザ作成 

```
$ mysql -u root -p
CREATE USER 'cacti'@'localhost' IDENTIFIED BY 'Cnetuser';
```

## cacti DB作成

```
$ CREATE DATABASE cacti;

MariaDB [(none)]> show databases;
+--------------------+
| Database           |
+--------------------+
| cacti              |
| information_schema |
| mysql              |
| performance_schema |
+--------------------+
4 rows in set (0.00 sec)
```

## cacti に cacti DBの権限付与

```
grant all on cacti.* to cacti@localhost identified by 'Cnetuser';
flush privileges;
```

## cacti DB に データ挿入

```
$ mysql -u cacti -p cacti < /usr/share/doc/cacti-1.2.19/cacti.sql
(Password Cnetuser)
```

## httpd 起動 & 自動起動有効 

```
$ systemctl enable httpd.service --now
```

## cacti.conf 設定変更

```
$ vi /etc/httpd/conf.d/cacti.conf

Alias /cacti    /usr/share/cacti

<Directory /usr/share/cacti/>
        <IfModule mod_authz_core.c>
                # httpd 2.4
-                Require host localhost
+                Require all grented
        </IfModule>
        <IfModule !mod_authz_core.c>
                # httpd 2.2
                Order deny,allow
                Deny from all
                Allow from localhost
        </IfModule>
</Directory>
```

## cacti DBの設定変更

```
$ vi /etc/cacti/db.php

$database_type     = 'mysql';
$database_default  = 'cacti';
$database_hostname = 'localhost';
$database_username = 'cacti';
$database_password = 'Cnetuser';
$database_port     = '3306';
$database_retries  = 5;
$database_ssl      = false;
$database_ssl_key  = '';
$database_ssl_cert = '';
$database_ssl_ca   = '';
$database_persist  = false;
```

## cron にpollerを登録

```
vi /etc/cron.d/cacti
*/5 * * * * cacti /usr/bin/php /usr/share/cacti/poller.php > /dev/null 2>&1
(既にいるのでコメント解除でOK)
```

## 設定できるとログインページが表示
(Chrome でサイトアクセス)

![loginpage](https://raw.githubusercontent.com/Linux-Database/image/main/login.jpg)

ユーザ名   admin
パスワード admin

## ログインできるとパスワード変更ページが表示
![changepass](https://raw.githubusercontent.com/Linux-Database/image/main/passchenge.jpg)

いまのパスワード (admin)
新しいパスワード (Cnetuser1_)

## パスワードが変更できると言語選択になるので［日本語］を選択してGPL への同意をチェック
![setup1](https://raw.githubusercontent.com/Linux-Database/image/main/setup/setup1.jpg)

## 次にインストール時のチェック画面が表示
各項目が警告などになっている箇所があるので、推奨値になるよう修正する。
![setup2](https://raw.githubusercontent.com/Linux-Database/image/main/setup/setup2.jpg)

## MySQL - Timezone Support がエラーなので、修正する
![setup2_error](https://raw.githubusercontent.com/Linux-Database/image/main/setup/setup2_error.jpg)

## タイムゾーンのテーブル作成 & データ挿入

```
$ mysql_tzinfo_to_sql /usr/share/zoneinfo | mysql -u root -p mysql
Enter password: 
Warning: Unable to load '/usr/share/zoneinfo/leapseconds' as time zone. Skipping it.
Warning: Unable to load '/usr/share/zoneinfo/tzdata.zi' as time zone. Skipping it.
```

## cacti にタイムゾーンテーブル権限付与

```
mysql -u root -p mysql
GRANT SELECT ON mysql.time_zone_name TO cacti@localhost;
flush privileges;
```

## /etc/php.ini を推奨値に設定変変更

```
vi /etc/php.ini

; Maximum amount of memory a script may consume (128MB)
; http://php.net/memory-limit
- memory_limit = 128M
+ memory_limit = 400M

; Maximum execution time of each script, in seconds
; http://php.net/max-execution-time
; Note: This directive is hardcoded to 0 for the CLI SAPI
- max_execution_time = 30
+ max_execution_time = 60
```

## /etc/my.cnf を推奨値に設定変更

```
$ vi /etc/my.cnf

[mysqld]
# Disabling symbolic-links is recommended to prevent assorted security risks
symbolic-links=0
character-set-server=utf8

+ collation_server=utf8mb4_unicode_ci
+ character_set_server=utf8mb4
+ character_set_client=utf8mb4
+ max_heap_table_size=512M
+ max_allowed_packet=16777216
+ tmp_table_size=128M
+ join_buffer_size=128M
+ innodb_file_per_table=ON
+ innodb_buffer_pool_size=1024M
+ innodb_doublewrite=OFF
+ innodb_flush_log_at_timeout=3
+ innodb_read_io_threads=32
+ innodb_write_io_threads=16
+ innodb_buffer_pool_instances=11
+ innodb_io_capacity=5000
+ innodb_io_capacity_max=10000
```

## DB再起動

```
$ systemctl restart mariadb
```

![setup2_ok](https://raw.githubusercontent.com/Linux-Database/image/main/setup/setup2_ok.jpg)
ページを更新してこのようになればOK

![setup3](https://raw.githubusercontent.com/Linux-Database/image/main/setup/setup3.jpg)
このまま次へ

![setup4](https://raw.githubusercontent.com/Linux-Database/image/main/setup/setup4.jpg)
今回は全てOKだった。何か警告が出ていれば修正する。

![setup5](https://raw.githubusercontent.com/Linux-Database/image/main/setup/setup5.jpg)
今回はバイナリパスは全てOKだった。何かエラーが出ていればインストールする。

![setup6](https://raw.githubusercontent.com/Linux-Database/image/main/setup/setup6.jpg)
チェックを付けて次へ

![setup7](https://raw.githubusercontent.com/Linux-Database/image/main/setup/setup7.jpg)
今回は、検証のために1分ごとに情報を取得するように設定した。

ネットワークは環境に合わせて 172.16.32.0/20 に設定した。

![setup8](https://raw.githubusercontent.com/Linux-Database/image/main/setup/setup8.jpg)
テンプテートの設定。今回は全てチェックマークに入れた。

![setup9](https://raw.githubusercontent.com/Linux-Database/image/main/setup/setup9.jpg)
DBに関する画面

![setup9_error](https://raw.githubusercontent.com/Linux-Database/image/main/setup/setup9_error.jpg)
DBの文字コードを変更する

```
$ mysql -u root -p
ALTER DATABASE cacti CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
```

![setup9_ok](https://raw.githubusercontent.com/Linux-Database/image/main/setup/setup9_ok.jpg)
このようになればOK

![setup10](https://raw.githubusercontent.com/Linux-Database/image/main/setup/setup10.jpg)
チェックマークを入れてインストールボタンを押すとインストールが開始される

![setup11](https://raw.githubusercontent.com/Linux-Database/image/main/setup/setup11.jpg)
インストールできた様子　始めるを押すとコンソールページに移動できる。

![toppage](https://raw.githubusercontent.com/Linux-Database/image/main/toppage.jpg)
正常にインストールできると、このような画面が表示される。

![graph](https://raw.githubusercontent.com/Linux-Database/image/main/graph.jpg)
グラフページを表示すると、このようにグラフが表示される。

## localhost の snmp 設定
![localhost_snmp_setup](https://raw.githubusercontent.com/Linux-Database/image/main/setup/localhost_snmp_setup.jpg)

コンソール > マネジメント > デバイス > Local Linux Machine 
SNMP Options の SNMP Version を "Not In Use" から "Version 2"に変更することで、SNMPで情報を取得できるようになる。
コミュニティ名をそれぞれ naka kaku に設定した。

## ディスク容量、ネットワークトラヒック量をグラフで表示

### ディスク容量

![snmp_graph1](https://raw.githubusercontent.com/Linux-Database/image/main/graph/snmp_disk1.jpg)

ディスク容量を見るには、SNMPで取得したデータをクエリーとして追加する必要がある。
マネジメント＞デバイス＞連想データ照会＞Add Data Query で Net-SNMP - Get Monitored Partitions を選択して追加ボタンをクリックする。

![snmp_disk2](https://raw.githubusercontent.com/Linux-Database/image/main/graph/snmp_disk2.jpg)

次に、対象のディスクデバイスを選択する。
作成＞新規グラフ＞デバイスを[Local Linux Machine]に選択
Data Query [Unix - Get Monitored Partitions] の /dev/xvda1 を選択して作成をクリック。

![snmp_graph1](https://raw.githubusercontent.com/Linux-Database/image/main/graph/snmp_graph1.jpg)
グラフに移動すると、ディスク容量を見ることができる。

### ネットワークトラヒック量

![snmp_network1](https://raw.githubusercontent.com/Linux-Database/image/main/snmp_network.jpg)
トラヒック量を見るには、SNMPで取得したデータをクエリーとして追加する必要がある。
マネジメント＞デバイス＞連想データ照会＞Add Data Query で SNMP - Interface Statistics を選択して追加ボタンをクリックする。

![snmp_graph2](https://raw.githubusercontent.com/Linux-Database/image/main/graph/snmp_graph2.jpg)
グラフに移動すると、トラヒック容量を見ることができる。

## 対向ホスト追加方法
今回は、対向の状態を監視できるように設定した。

### 対向ホスト追加
今回は、naka から kaku を追加する方法を説明する。

![hostadd1](https://raw.githubusercontent.com/Linux-Database/image/main/hostadd/hostadd1.jpg)
コンソール＞作成＞New Device でホストを追加することができる。
名前、ホスト名、デバイステンプレート、SNMPバージョン、コミュニティ名を設定したら作成をクリック

![hostadd1_ok](https://raw.githubusercontent.com/Linux-Database/image/main/hostadd/hostadd1_ok.jpg)
作成出来ると、このような出力がされる。

![hostadd2](https://raw.githubusercontent.com/Linux-Database/image/main/hostadd/hostadd2.jpg)
コンソール＞マネジメント＞デバイス　に移動すると、kaku が追加できていることが分かる。

![hostadd3](https://raw.githubusercontent.com/Linux-Database/image/main/hostadd/hostadd3.jpg)
ディスク容量とネットワークトラヒック量をグラフで表示するために、
kaku をクリック。
連想データ照会＞Add Data Query > Net-SNMP - Get Monitored Partitions と SNMP - Interface Statistics を追加する。

![hostad4](https://raw.githubusercontent.com/Linux-Database/image/main/hostadd/hostad4.jpg)
次に、コンソール＞作成＞新規グラフで、
Data Query [SNMP - Get Mounted Partitions] の / と
Data Query [SNMP - Interface Statistics] の eth 0 に チェックを入れて作成をクリック。

![hostadd5](https://raw.githubusercontent.com/Linux-Database/image/main/hostadd/hostadd5.jpg)
グラフ＞Default Tree > local > Machine > kaku をクリックすると、ディスク容量とネットワークトラヒック量を見ることができた。
