# 网络排查命令
## 1.基础概念 ##
用于排查服务器网络不通、端口不通、服务无法访问、网络延迟等问题。

## 2.常用网络命令 ##
```bash
# 查看本机所有正在监听的端口和对应服务
ss -tulnp

# 查看指定端口被哪个进程占用
sudo lsof -i :端口号

# 测试目标IP和端口是否能连通
nc -zv 服务器IP 端口号

# 追踪路由，查看网络延迟节点
traceroute 域名或IP
```

## 3.常见故障排查 ##
```bash
# 服务无法启动
systemctl status 服务名
journalctl -xe 查看详细错误

# 远程端口连不上
检查防火墙 ufw 规则
用 nc -zv 测试端口连通性

# 端口被占用
lsof -i 查看占用进程
kill PID 关闭进程

# 网站无法访问
查看Nginx运行状态
curl localhost 本地测试访问
```