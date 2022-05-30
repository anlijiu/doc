### 常用命令

+ 查看编译某个包需要依赖哪些开发包
  ``` shell
  apt-rdepends --build-depends --follow=DEPENDS dunst
  # 或者
  sudo apt -s build-dep dunst
  ```
+ 直接安装编译某个包需要依赖的开发包
  ``` shell
  sudo apt build-dep dunst
  ```
+ 查看系统硬件信息
  ```
  sudo apt install inxi
  inxi -Fazy
  ```

+ 查看systemd 服务从哪里找寻 *.service文件
  ``` shell
  systemctl --no-pager --property=UnitPath show | tr ' ' '\n'
  # 查看某个 service 状态
  sudo systemctl status dunst.service
  ```
+ 查看某个文件属于哪个包
  ``` shell
  dpkg -S notify-send
  # 或者 
  # sudo apt install apt-file
  # sudo apt-file update
  # apt-file search notify-send
  ```
+ 创建删除虚拟网卡
  ```
  sudo ifconfig enp0s31f6:0 192.168.21.228 up
  sudo ifconfig enp0s31f6:0 down
  ```
+ 显示所有用户及uid
  ```
  cut -d ':' -f 1,3 /etc/passwd | sort -t ':' -k2n - | tr ':' '\t'
  ```
+ 查看进程使用内存状况
  ```
  ps aux | awk '{if ($5 != 0 ) print $2,$5,$6,$11}' | sort -k2n
  # PID VSZ RSS COMMAND
  # 升序， 最下面的占用最大
  ```
+ 找到top 10 最大文件
  ```
  du -sk /var/log/* | sort -r -n | head -10
  ```
+ 找到top 10 最常用命令(.bash_history)
  ```
  cat ~/.bash_history | tr "\|\;" "\n" | sed -e "s/^ //g" | cut -d " " -f 1 | sort | uniq -c | sort -n | tail -n 15
  ```
+ 查看ascii
  ```
  man ascii
  ```
+ 查看&修改系统时区
  ```
  timedatectl status
  timedatectl set-timezone "Asia/Shanghai"
  ```

### gnome 常用设置

##### 设置dock panel 在屏幕底部

``` shell
gsettings set org.gnome.shell.extensions.dash-to-dock extend-height false
gsettings set org.gnome.shell.extensions.dash-to-dock dock-position BOTTOM
gsettings set org.gnome.shell.extensions.dash-to-dock transparency-mode FIXED
gsettings set org.gnome.shell.extensions.dash-to-dock  apply-custom-theme true
gsettings set org.gnome.shell.extensions.dash-to-dock dash-max-icon-size 48
gsettings set org.gnome.shell.extensions.dash-to-dock unity-backlit-items true

# reset 设置
gsettings reset org.gnome.shell.extensions.dash-to-dock dash-max-icon-size
```

### gnome 常用快捷键
+ 截屏图片
  ```
  Print          // 鼠标选择交互截屏
  Alt + Print    // 截屏窗口
  Shift + Print  // 截屏
  ``` 
+ 截屏录像
  ``` 
  Ctrl + Alt + Shift + R
  ```
+ 窗口最大化
  ```
  Super + ↑
  ```
+ 窗口最小化(Hide Window)
  ```
  Super + H
  ```
+ 窗口正常化(不大不小)
  ```
  Super + ↓
  ```
+ 窗口占左半边
  ```
  Super + ←
  ```
+ 窗口占右半边
  ```
  Super + →
  ```
+ 窗口移动到下一个工作区
  ```
  Super+Shift+PgDown
  ```
+ 窗口移动到上一个工作区
  ```
  Super+Shift+PgUp
  ```
+ 跳转到下一个工作区
  ```
  Ctrl + Shift + →
  ```
+ 跳转到上一个工作区
  ```
  Ctrl + Shift + ←
  ```
+ Zoom 屏幕
  ```
  Alt+Super+8
  ```
+ 查看app列表和所有窗口overview
  ```
  Super + A
  ```
+ 最小化所有窗口(回到Desktop)
  ```
  Ctrl + Alt + d
  ```
+ 显示(关闭)通知面板
  ```
  Super + V
  ```


### shell 常用快捷键
+ 回到行首
  ```
  Ctrl + A
  ```
+ 回到行尾
  ```
  Ctrl + E
  ```
+ 清除屏幕(等同于clear命令)
  ```
  Ctrl + L
  ```
+ 跳到下一个单词
  ```
  Alt + F
  ```
+ 跳到上一个单词
  ```
  Alt + B
  ```
+ 删除光标之前所有内容
  ```
  Ctrl + U
  ```
+ 删除光标之后所有内容
  ```
  Ctrl + K
  ```
+ 删除光标之前的一个单词
  ```
  Ctrl + W
  ```
+ 删除光标之后的一个单词
  ```
  Alt + D
  ```
+ 恢复快捷键删除的内容，粘贴到光标处
  ```
  Ctrl + Y
  ```
+ 查看历史命令
  ```
  Ctrl + R
  ```

### update-alternatives
  ```
  # 创建 /usr/local/bin/python 连接， 指向 /usr/bin/python2
  sudo update-alternatives --install /usr/local/bin/python python /usr/bin/python2 20
  sudo update-alternatives --install /usr/local/bin/python python /usr/bin/python3 10

  # 选择python 2 / 3
  sudo update-alternatives --config python
  ```
