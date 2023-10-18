
由于 ubuntu20.04 默认是python3.8，因此3.9需要再安装 

### 1. 拉取基础镜像
```
docker pull ubuntu:20.04
```

### 2. 启动容器
```
docker run -it -e LANG=C.UTF-8 ubuntu:20.04 
```

### 3. 进入容器后进行安装
```
# 修改 apt源
sed -i 's@http://archive.ubuntu.com/ubuntu/@http://mirrors.aliyun.com/ubuntu/@g' /etc/apt/sources.list

apt update
apt install -y curl wget vim  # 安装常见软件
apt install python3.9  
apt install -y python3-distutils

curl 'https://bootstrap.pypa.io/get-pip.py' > get-pip.py   #  下载 pip
python3.9 get-pip.py  # 安装pip

ln -s /usr/bin/python3.9 /usr/bin/python  # 建立软连接

# 验证安装
python --version
pip --version
```

### 4. 容器转为image
```
docker commit <container-id> ubuntu_py39:20.04
```

参考资料
1. https://www.cnblogs.com/lihouqi/p/16267795.html
2. https://cclc.github.io/docker/ubuntu20.04-install-python3.9.html#_2-%E5%90%AF%E5%8A%A8%E5%AE%B9%E5%99%A8
3. https://stackoverflow.com/questions/39790923/python-cant-open-file-get-pip-py-error-2-no-such-file-or-directory
4. https://blog.csdn.net/qq_20466211/article/details/128731196