# 压缩与打包

### 1. gzip 命令
```bash
# gzip 仅压缩单个文件，不支持目录，压缩后原文件消失
gzip file.txt        # 压缩：file.txt → file.txt.gz
gunzip file.txt.gz   # 解压：file.txt.gz → file.txt
gzip -d file.txt.gz  # 等价于gunzip，-d表示解压
```
### 2.zip命令 ###
```bash
# zip 支持目录压缩，兼容Windows，压缩后原文件保留
zip -r archive.zip dir/  # -r：递归压缩目录（必须加，否则只压缩目录名）
zip file.zip file1.txt file2.txt  # 压缩多个文件到一个包

# unzip 解压zip包
unzip archive.zip        # 解压到当前目录
unzip archive.zip -d /tmp/ # 解压到指定目录/tmp
unzip -l archive.zip     # 查看压缩包内容（不解压）
```

### 3.tar命令 ###
```bash
# tar 核心参数解释：
# c = create（创建打包文件）
# z = gzip（启用gzip压缩/解压）
# f = file（指定输出/输入文件名）
# x = extract（提取/解压文件）
# v = verbose（显示压缩/解压过程）
# t = list（查看压缩包内容，不解压）

# 打包并gzip压缩（基础版，不显示过程）
tar -czf output.tar.gz target_dir/

# 打包并gzip压缩（显示过程版，v参数）
tar -czvf output.tar.gz target_dir/

# 解压gzip压缩包（基础版）
tar -xzf file.tar.gz

# 解压到指定目录
tar -xzf file.tar.gz -C /tmp/

# 查看压缩包内容（不解压）
tar -tf file.tar.gz

# 仅打包不压缩
tar -cf output.tar target_dir/

# 解压未压缩的tar包
tar -xf output.tar
```