# Nginx 常见故障排错训练
## 1.网页打不开 ##
```bash
# 确认Nginx服务状态
sudo systemctl status nginx

# 确认80端口监听
ss -tulnp | grep 80

# 本机测试访问
curl -i http://127.0.0.1

# 确认首页文件存在
ls -la /var/www/html/index.html

# 修复文件权限
sudo chmod 644 /var/www/html/index.html
```

## 2.Nginx 起不来 ##
```bash
# 查看服务状态
sudo systemctl status nginx

# 尝试启动
sudo systemctl start nginx

# 查看详细错误日志
sudo journalctl -u nginx -e
sudo tail -f /var/log/nginx/error.log

# 测试配置语法
sudo nginx -t

# 修复后重启
sudo systemctl restart nginx
```

## 3.端口被占用（80 端口冲突） ##
```bash
# 查看80端口占用
ss -tulnp | grep 80
sudo lsof -i :80

# 杀掉占用进程
sudo kill PID

# 强制终止
sudo kill -9 PID

# 重启Nginx
sudo systemctl restart nginx
```

## 4.权限不足（文件权限修复） ##
```bash
# 查看文件权限
ls -la /var/www/html/index.html

# 修复权限
sudo chmod 644 /var/www/html/index.html

# 确认Nginx用户可读取
sudo -u www-data cat /var/www/html/index.html
```

## 5. 防火墙拦截（端口放行） ##
```bash
# 查看防火墙状态
sudo ufw status

# 开放80端口
sudo ufw allow 80

# 重载防火墙
sudo ufw reload
```

##  6. 日志查看（排错核心） ##
```bash
# 实时查看访问日志
sudo tail -f /var/log/nginx/access.log

# 实时查看错误日志
sudo tail -f /var/log/nginx/error.log
```