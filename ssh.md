### 生成ssh秘钥对
```
ssh-keygen -t rsa
```

### 实现免密登录
ssh-copy-id命令可以把本地主机的公钥复制到远程主机的authorized_keys文件上，实现免密登录远程主句
```
ssh-copy-id -i ~/.ssh/id_rsa.pub user@ip
```

### 给远程主机命名一个通俗易懂的名字
修改/etc/hosts文件
```
10.96.80.11 hadoop001
```

### 修改本机hostname（目的只是为了让terminal显示主机名时更通俗易懂，但效果只在本机有用）
显示当前主机名
```
host
```
修改主机名
```
host 主机名
```
