# SSH 远程连接
## 1.基础概念 ##
SSH 是安全远程连接协议，加密传输数据，替代不安全的 telnet，支持密码登录和密钥登录，是服务器管理核心工具。

## 2.服务安装与启动 ##
```bash
# 安装SSH服务端
sudo apt install openssh-server -y

# 启动SSH服务
sudo systemctl start ssh

# 设置SSH开机自启
sudo systemctl enable ssh

# 查看SSH运行状态
sudo systemctl status ssh
```

## 3.密钥登录配置 ##
```bash
# 生成4096位RSA密钥对，更安全
ssh-keygen -t rsa -b 4096

# 将本地公钥复制到服务器，实现免密登录
ssh-copy-id 用户名@服务器IP

# 远程登录服务器
ssh 用户名@服务器IP
```

## 4.关键文件路径 ##
```bash
# 本地私钥，必须严格保密，不可泄露
~/.ssh/id_rsa

# 本地公钥，可上传到服务器
~/.ssh/id_rsa.pub

# 服务器存放授权公钥的文件
~/.ssh/authorized_keys
```

## 5.密钥登录原理 ##
服务器用公钥加密随机数，客户端用私钥解密后返回，服务器验证一致则允许登录，全程加密，无密码泄露风险。
