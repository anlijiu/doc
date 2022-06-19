
``` shell
# 安装依赖项 libssl1.1
echo "deb http://security.ubuntu.com/ubuntu jammy-security main" | sudo tee /etc/apt/sources.list.d/jammy-security.list
sudo apt update
sudo apt install libssl1.1
```

``` shell
# 安装mongodb 社区版
wget -qO - https://www.mongodb.org/static/pgp/server-5.0.asc | sudo apt-key add -
sudo touch /etc/apt/sources.list.d/mongodb-org-5.0.list
sudo echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/5.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-5.0.list

sudo apt install mongodb-org
```

``` shell
# 查看init system 是systemd (which uses the systemctl command)
# 还是older versions of Linux tend to use System V init (which uses the service command).
ps --no-headers -o comm 1
# systemd
# 启动mongod 服务
sudo systemctl start mongod

#查看服务状态
sudo systemctl status mongod

# enable 服务
sudo systemctl enable mongod
```


``` shell
# 查看端口号 27017
netstat -alntup | grep 27017
```

### mongodb gui client
参照 [best-mongodb-gui-client](https://www.softwaretestinghelp.com/best-mongodb-gui-client/)
选用[MongoDB Compass](https://www.mongodb.com/try/download/compass)
下载deb  
sudo dpkg -i mongodb-compass_1.32.2_amd64.deb
报错有依赖没有安装 , 执行安装所有缺失依赖
sudo apt install --fix-broke 

