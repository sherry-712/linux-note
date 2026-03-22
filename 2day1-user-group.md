# 用户与组深入

## 查看用户身份
### 1. id 命令（查看UID/GID/所属组）
```bash
# 查看当前用户信息
id
# 输出示例：uid=1000(ubuntu) gid=1000(ubuntu) groups=1000(ubuntu),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),101(lxd)
# 说明：1000号用户，属于sudo组，具备sudo权限

# 查看指定用户信息
id user1
# 输出示例：uid=1001(user1) gid=1001(user1) groups=1001(user1)
# 说明：user1仅在自身组，无sudo权限
```

### 2. groups 命令（查看所属组）
```bash
# 查看当前用户所属组
groups
# 输出示例：ubuntu adm cdrom sudo dip plugdev lxd

# 查看指定用户所属组
groups user1
# 输出示例：user1:user1
# 说明：冒号前是用户名，冒号后是所属组
```

### 3. su 命令（切换用户）
```bash
# 仅切换用户，不切换环境（exit返回，logout无效）
su user1

# 切换用户并切换环境（exit/logout均可返回）
su - user1
```

### 4. sudo 命令（以 root 权限执行） 
```bash
# 验证是否有sudo权限（输出root则有）
sudo whoami

# 切换用户后验证当前用户
whoami
# 输出示例：user1
```

### 5. usermod 命令（修改用户属性）
```bash
# 将user1追加到sudo组（-aG避免覆盖原有组）
sudo usermod -aG sudo user1
```