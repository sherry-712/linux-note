# 进程管理

## 查看进程
### 1. 静态查看
```bash
# ps aux：查看所有进程（ps = process status）
#（a=所有用户，u=用户信息，x=无终端进程）
# PID：进程唯一标识
ps aux

# pstree：以树状结构展示进程父子关系
pstree

# ps aux | grep 关键词：过滤指定进程
# 注意：grep 自身也会出现在结果中（可加 | grep -v grep 排除）
ps aux | grep ssh
ps aux | grep ssh | grep -v grep  # 排除grep自身进程

# 进程排序（命令行方式）
ps aux --sort=-rss  # 按内存使用率降序排列
ps aux --sort=-pcpu # 按CPU使用率降序排列
```

### 2.动态监视 ###
```bash
# top：实时监控进程（默认按 CPU 排序）
# 快捷键：M（按内存）、P（按 CPU）、T（按运行时间）、q (退出)
top

# htop：更美观、交互性更强的top增强版（需先安装：sudo apt install htop）
htop
```

## 后台任务管理 ##
```bash
# &：直接在后台运行命令
command &

# Ctrl+Z：暂停当前前台任务（快捷键）

# bg %编号：让暂停的任务在后台继续运行
bg %1

# fg %编号：把后台任务调回前台
fg %1

# jobs：查看后台任务列表
jobs

# kill：终止指定进程
kill PID

#强制杀进程
kill -q PIN

#按名字杀进程
pkill

```