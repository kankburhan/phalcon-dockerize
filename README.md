# docker-compose-php-nginx-mysql-redis
## How to use
> docker-compose up --build

## In PHP File

### Rredis use in php
```
 $redis = new Redis();
 $redis->connect('redis', 6379);
 echo "Connection to server sucessfully";
 $redis->set("tutorial-name", "Redis tutorial");
 echo "Stored string in redis:: " . $redis->get("tutorial-name");
```

### Mysql use in php
```
$servername = 'mysql';
$username = 'root';
$password = 'root';

$mysql = new MySQLi($servername, $username, $password, 'wordpress');
if ($mysql->connect_errno) {
echo "Errno: " . $mysql->connect_errno . "\n";
}
$result = $mysql -> query("show databases");
print_r($result);
```


### Add User Mysql 
Tambahkan Grant Access ke mysql

```
CREATE USER 'admin'@'localhost' IDENTIFIED WITH mysql_native_password BY 'admin';
GRANT ALL PRIVILEGES ON *.* TO 'admin'@'localhost' WITH GRANT OPTION;
CREATE USER 'admin'@'%' IDENTIFIED WITH mysql_native_password BY 'admin';
GRANT ALL PRIVILEGES ON *.* TO 'admin'@'%' WITH GRANT OPTION;
#
CREATE DATABASE IF NOT EXISTS `kd-chat` COLLATE 'utf8_general_ci' ;
GRANT ALL ON `kd-chat`.* TO 'admin'@'%' ;
FLUSH PRIVILEGES ;
```
