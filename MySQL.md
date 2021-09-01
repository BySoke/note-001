# 一.MySQL相关插件

## 1.MySQL安装

- [官网地址](https://dev.mysql.com/downloads/mysql/)

- 根目录下新建my.ini及data文件夹

  ```ini
  [client] port=3306 
  default-character-set=utf8 [mysqld]  
  # 设置为自己MYSQL的安装目录  
  basedir=D:MySQLmysql-5.7.28-winx64 
  # 设置为MYSQL的数据目录  
  datadir=D:MySQLmysql-5.7.28-winx64data 
  port=3306 
  character_set_server=utf8 
  sql_mode=NO_ENGINE_SUBSTITUTION,NO_AUTO_CREATE_USER 
  #开启查询缓存 
  explicit_defaults_for_timestamp=true 
  skip-grant-tables
  ```

- 新建变量

  ```apl
  MYSQL_HOME=D:MySQLmysql-5.7.28-winx64
  path变量中添加%MYSQL_HOME%bin 
  ```

- 进入Mysql安装目录下的bin文件夹，在此处以管理员身份打开cmd,执行 

  ```shell
  mysqld --initialize
  ```

- 若出现

  ```shell
  error:Found option without preceding group in config file: D:Mysqlmysql-5.7.19-winx64my.ini at line: 1   
  ```

  [^]: 解决方法:把my.ini保存为ANSI格式

- 执行

  ```shell
  mysqld install
  net start MySQL
  ```

  [^]: 因为my.ini中加入了skip-grant-tables配置，可以直接使用  mysql -u root -p  输入任意密码登录

  ```
  mysql -u root -p 123456
  USE mysql;
  update user set authentication_string=PASSWORD('123456') where user='root';
  flush privileges;
  exit;
  ```

- 把my.ini中的#skip-grant-tables 注释掉

  ```shell
  net stop mysql;
  net start mysql;
  mysql -uroot -p123456;
  show databases;
  ```

  可能会报错  

  ```shell
  ERROR 1820 (HY000): You must reset your password using ALTER USER statement before executing this statement.
  ```

  ```sql
  alter user user() identified by "123456"; exit;mysql -uroot -p123456;  
  show databases;
  ```

  

