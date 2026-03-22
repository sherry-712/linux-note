# 文件查找

## 实时搜索
### 1. find 命令（精准但慢，实时遍历目录树）
```bash
# 按名称查找.conf后缀文件（忽略权限错误，取前20条）
find / -name "*.conf" 2>/dev/null | head -20

# 按大小查找（+表示大于，-表示小于，单位：K/M/G）
find / -size +100M 2>/dev/null | head -20  # 大于100MB
find / -size -10K 2>/dev/null | head -20   # 小于10KB

# 按修改时间查找（-表示多久内，+表示多久前，单位：天）
find / -mtime -7 2>/dev/null | head -20    # 7天内修改过的文件
find / -mtime +30 2>/dev/null | head -20   # 30天前修改过的文件

# 按权限查找（补充常用场景）
find / -perm 777 2>/dev/null | head -20    # 查找权限为777的文件

```

### 2.grep命令（搜文件内容） ###
```bash
# grep 核心特点：搜索文件内的文本内容，支持正则表达式
# -r：递归搜索目录下所有文件（包含子目录）
# -i：忽略大小写
# -n：显示匹配行的行号
grep -r "error" /var/log/ 2>/dev/null        # 搜索含error的行
grep -rn "ERROR" /var/log/ 2>/dev/null       # 显示行号
grep -rin "error" /var/log/ 2>/dev/null      # 忽略大小写+显示行号
```

## 快速查找
### 1.which命令 ###
```bash
# which 仅查找系统PATH环境变量中的可执行命令
which ls          # 输出示例：/usr/bin/ls
which grep       # 输出示例：/usr/bin/grep
which python3    # 输出示例：/usr/bin/python3
```
### 2. whereis 命令（快，查命令的二进制 / 源码 / 手册页）###
```bash
whereis ls       # 输出示例：ls: /usr/bin/ls /usr/share/man/man1/ls.1.gz
whereis grep     # 输出示例：grep: /usr/bin/grep /usr/share/man/man1/grep.1.gz
```
### 3. locate 命令（秒级搜索，依赖数据库）###
```bash
# locate 核心特点：基于数据库搜索，速度极快，但结果可能不是实时的
# 第一步：更新文件名数据库（需sudo权限，扫描整个系统）
sudo updatedb

# 第二步：快速查找文件（支持模糊匹配）
locate .bashrc   # 查找所有包含.bashrc的文件
locate passwd    # 查找所有包含passwd的文件
locate /etc/hosts # 精准查找指定路径文件
```