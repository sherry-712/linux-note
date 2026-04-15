# 系统日志查看
## 1.基础概念 ##
日志是服务器排错核心，记录系统、服务、登录、硬件所有运行状态，出问题优先看日志。

## 2.常用日志命令 ##
```bash
# 实时跟踪系统日志，刷新显示最新内容
tail -f /var/log/syslog

# 查看系统详细日志，带解释，跳转到最新
journalctl -xe

# 只查看Nginx服务日志
journalctl -u nginx

# 只查看今天产生的所有日志
journalctl --since today

# 查看内核日志，筛选错误信息
dmesg | grep error

# 查看历史成功登录记录
last

# 查看失败登录记录（暴力破解）
lastb
```

## 3.重要日志文件 ##
```bash
# 系统全局综合日志，所有服务运行信息
/var/log/syslog

# 认证日志，SSH登录、sudo授权、账号登录失败
/var/log/auth.log

# 内核日志，硬件、驱动、系统内核报错
/var/log/kern.log
```