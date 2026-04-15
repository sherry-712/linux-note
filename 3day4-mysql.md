# MySQL 数据库
## 1.基础概念 ##
MySQL 是开源关系型数据库，用于存储网站、应用数据，是 Linux 服务器最常用数据库之一。

## 2.安装与启动 ##
```bash
# 更新软件源
sudo apt update

# 安装MySQL服务
sudo apt install mysql-server -y

# 启动MySQL
sudo systemctl start mysql

# 设置MySQL开机自启
sudo systemctl enable mysql

# 查看MySQL运行状态
sudo systemctl status mysql
```

## 3.安全配置与登录 ##
```bash
# MySQL安全初始化，设置密码、删除匿名用户、禁止远程root登录
sudo mysql_secure_installation

# 登录MySQL数据库
sudo mysql -u root -p

# 退出MySQL
EXIT;
```

## 4.关键文件路径 ##
```bash
# MySQL配置文件目录
/etc/mysql/mysql.conf.d/

# 数据库数据存储目录
/var/lib/mysql

# MySQL错误日志，启动失败查看
/var/log/mysql/error.log

# MySQL本地连接Socket文件
/var/run/mysql/mysql.sock
```