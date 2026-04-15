# Flask项目部署（Nginx+Gunicorn+Systemd）

## 1.部署架构与核心组件 ##
请求流程：浏览器 → Nginx（80端口）→ Gunicorn（5000端口）→ Flask
Flask：Python Web框架，处理业务逻辑
Gunicorn：WSGI服务器，运行Python应用
Nginx：反向代理，接收外部请求、转发给Gunicorn
虚拟环境：隔离项目依赖，避免版本冲突、多项目不干扰
Systemd：管理服务，开机自启、进程守护

## 2.关键文件位置 ##
```bash
# Flask应用代码
~/flask_app/app.py
# 虚拟环境目录
~/flask_app/myenv/
# Nginx站点配置
/etc/nginx/sites-available/flask_app
# 已启用站点
/etc/nginx/sites-enabled/flask_app
# Systemd服务文件
/etc/systemd/system/flask_app.service
```

## 3.Python 环境准备 ##
```bash
# 安装Python3和虚拟环境工具
sudo apt install python3 python3-venv -y

# 创建项目目录
mkdir -p ~/flask_app
cd ~/flask_app

# 创建虚拟环境
python3 -m venv myenv

# 激活虚拟环境
source myenv/bin/activate

# 退出虚拟环境
deactivate
```

## 4. 安装 Gunicorn ##
```bash
# 在激活的虚拟环境中安装
pip install gunicorn
```

## 5. 运行 Flask 项目 ##
```bash
# 开发模式（仅测试）
python app.py

# 生产模式（Gunicorn后台运行）
gunicorn --bind 0.0.0.0:5000 app --daemon

# 停止Gunicorn
pkill gunicorn
```

## 6.Nginx 配置 ##
```bash
# 创建Nginx站点配置
sudo nano /etc/nginx/sites-available/flask_app

# 启用站点（创建软链接）
sudo ln -s /etc/nginx/sites-available/flask_app /etc/nginx/sites-enabled/

# 移除默认站点
sudo rm /etc/nginx/sites-enabled/default

# 测试Nginx配置语法
sudo nginx -t

# 重启Nginx
sudo systemctl restart nginx
```

## 7.Systemd 服务配置 ##
```bash
# 创建Systemd服务文件
sudo nano /etc/systemd/system/flask_app.service

# 重新加载Systemd配置
sudo systemctl daemon-reload

# 启动Flask服务
sudo systemctl start flask_app

# 设置开机自启
sudo systemctl enable flask_app

# 查看服务状态
sudo systemctl status flask_app
```