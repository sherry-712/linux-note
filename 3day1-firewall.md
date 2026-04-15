# 防火墙 ufw
## 1.基础概念 ##
ufw 是 Ubuntu 默认的防火墙工具，底层基于 iptables，用于控制服务器端口访问与网络安全，防止未授权访问。

## 2.常用操作命令 ##
```bash
# 开启防火墙并设置开机自启
sudo ufw enable

# 关闭防火墙并关闭开机自启
sudo ufw disable

# 查看防火墙当前状态与规则列表
sudo ufw status

# 查看防火墙详细状态（默认策略+日志+规则）
sudo ufw status verbose

# 带编号查看防火墙规则，方便精准删除
sudo ufw status numbered

# 根据编号删除指定防火墙规则
sudo ufw delete 编号

# 允许指定IP地址访问本机所有端口
sudo ufw allow from IP地址

# 拒绝外部访问指定端口
sudo ufw deny 端口号

# 重置防火墙，清空所有自定义规则，恢复默认
sudo ufw reset
```

## 3.常用端口放行 ##
```bash
# tee 核心作用：读取管道输入，一份输出到屏幕，一份写入文件
ls -l / | tee list.txt  # 屏幕显示+写入list.txt

# tee -a：追加写入文件（不覆盖）
ls -l /home | tee -a list.txt

# 同时写入多个文件
ls -l /etc | tee file1.txt file2.txt
```