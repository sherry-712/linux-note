# Nginx 服务
## 1.基础概念 ##
Nginx 是高性能 Web 服务器，用于搭建网站、反向代理、负载均衡，占用资源低、并发能力强。

## 2.安装与服务管理 ##
```bash
# 安装Nginx
sudo apt install nginx -y

# 启动Nginx服务
sudo systemctl start nginx

# 设置Nginx开机自启
sudo systemctl enable nginx

# 查看Nginx运行状态
sudo systemctl status nginx

# 测试Nginx配置文件是否正确
nginx -t
```

## 3.核心配置与日志路径 ##
```bash
# Nginx 主配置文件
/etc/nginx/nginx.conf

# 可用站点配置文件目录
/etc/nginx/sites-available

# 已启用站点软链接目录
/etc/nginx/sites-enabled

# 默认网站根目录，存放网页文件
/var/www/html

# 访问日志，记录所有用户访问请求
/var/log/nginx/access.log

# 错误日志，服务启动失败、页面报错时查看
/var/log/nginx/error.log
```

## 4.常见问题排查 ##
配置文件错误 → 用 nginx -t 检查语法
网页打不开 → 查看 80/443 端口是否监听、防火墙是否放行
启动失败 → 查看 error.log 定位原因