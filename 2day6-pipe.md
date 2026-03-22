# 管道和重定向

## 基础概念
### 1. 文件描述符
```bash
# 标准输入：0（键盘输入）
# 标准输出：1（屏幕正常输出）
# 错误输出：2（屏幕错误提示）
```
### 2.输出重定向
```bash
# >：覆盖输出（清空文件后写入）
echo "hello" > file.txt

# >>：追加输出（在文件末尾添加）
echo "world" >> file.txt

# 2>：重定向错误信息到文件
find / -name "*.conf" 2>error.log

# 正常结果和错误信息分开存储
find / -name "*.conf" > result.txt 2>error.log

# 2>&1：将错误输出合并到标准输出
find / -name "*.conf" > all.txt 2>&1

# 丢弃所有输出
find / -name "*.conf" > /dev/null 2>&1

# 仅丢弃错误输出
find / -name "*.conf" 2>/dev/null

# &>：重定向所有输出（标准+错误）
find / -name "*.conf" &> all.log

# <：输入重定向（从文件读取输入，替代键盘）
cat < file.txt  # 等价于 cat file.txt
wc -l < file.txt # 统计file.txt的行数
```
### 3.管道符| ###
```bash
# 过滤 ssh 相关进程
ps aux | grep ssh

# 取前10条进程信息
ps aux | head -10

# 统计进程数量
ps aux | wc -l

# 根目录文件夹大小排序（忽略错误）
du -sh /* 2>/dev/null | sort -h
```

### 4.tee命令 ###
```bash
# tee 核心作用：读取管道输入，一份输出到屏幕，一份写入文件
ls -l / | tee list.txt  # 屏幕显示+写入list.txt

# tee -a：追加写入文件（不覆盖）
ls -l /home | tee -a list.txt

# 同时写入多个文件
ls -l /etc | tee file1.txt file2.txt
```