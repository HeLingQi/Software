## 下载文件


```shell
wget -O /usr/local/bin/qbittorrent-nox -c 'https://github.com/Vicshs/Software/raw/main/Linux/qBittorrent/qbittorrent-nox'
chmod 755 /usr/local/bin/qbittorrent-nox
```




## 写入 systemd 文件

```shell
cat << EOF > /etc/systemd/system/qbittorrent.service
[Unit]
Description=qBittorrent Daemon Service
After=network.target

[Service]
LimitNOFILE=512000
User=root
ExecStart=/usr/local/bin/qbittorrent-nox
ExecStop=/usr/bin/killall -w qbittorrent-nox

[Install]
WantedBy=multi-user.target

EOF
```

## 初始化 qBittorrent 并开机启动

执行 `qbittorrent-nox` ，输入 y 并回车以确认使用协议。然后使用 Ctrl + C 键退出。
执行 `systemctl enable qbittorrent` 以使 qBittorrent 开机启动；
执行 `systemctl start qbittorrent` 以使 qBittorrent 在后台运行。

停止 qBittorrent 进程： `systemctl stop qbittorrent`；
取消 qBittorrent 开机启动： `systemctl disable qbittorrent`。



## 访问

访问 `http://服务器公网IP地址:8080/` ，输入 Web UI 的初始用户名 `admin` 和初始密码 `adminadmin`





/root/.local/share/data/qBittorrent/