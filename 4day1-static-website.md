# 部署静态网站
## 1.核心文件位置 ##
- 网站根目录：/var/www/html/
- 首页默认文件：/var/www/html/index.html
- Nginx 主配置文件：/etc/nginx/nginx.conf
- 站点配置文件：/etc/nginx/sites-available/default
- 访问日志：/var/log/nginx/access.log
- 错误日志：/var/log/nginx/error.log

## 2.完整部署流程 ##
```bash
# 查看服务器IP地址
ip addr

# 编辑首页网页文件
sudo nano /var/www/html/index.html

# 查看Nginx运行状态
sudo systemctl status nginx

# 重启Nginx
sudo systemctl restart nginx

# 测试静态网站访问
curl -i http://127.0.0.1
```

