###### 查看权限

ls -l 文件名         # 查看文件权限、所有者、组

权限数字对应：读(r)=4，写(w)=2，执行(x)=1，无权限=0

常用组合：rwx(7)、rw-(6)、r-x(5)、r--(4)、---(0)



###### 修改权限（数字法）

chmod 755 文件名     # 所有者rwx，组r-x，其他r-x
chmod 644 文件名     # 所有者rw-，组r--，其他r--



###### 修改权限（字母法）

chmod u+x 文件名     # 给所有者加执行权限
chmod g-w 文件名     # 给所属组去掉写权限
chmod o=r 文件名     # 给其他人设置只读权限
chmod a+x 文件名     # 给所有人加执行权限



###### 用户/组管理

sudo useradd 用户名   # 创建用户
sudo passwd 用户名    # 设置/修改用户密码
ls /home             # 查看所有用户家目录
su - 用户名          # 切换用户
sudo userdel -r 用户名 # 删除用户及家目录

sudo groupadd 组名    # 创建组
sudo usermod -aG 组名 用户名 # 把用户加入组（-a必须加，否则覆盖原有组）
sudo groupdel 组名    # 删除组



###### 修改文件所有者/组

sudo chown 用户名 文件名    # 修改文件所有者
sudo chown :组名 文件名     # 修改文件所属组
sudo chown 用户名:组名 文件名 # 同时修改所有者和组

