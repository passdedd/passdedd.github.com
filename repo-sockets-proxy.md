```
sudo apt-get install python-socksipy
```

#### add to repo 
```
import socks
import socket
socks.setdefaultproxy(socks.PROXY_TYPE_SOCKS5, "127.0.0.1", 1080)
socket.socket = socks.socksocket
```

#### for git protol

get connect.c from
https://bitbucket.org/gotoh/connect/downloads/

make

cp connect /usr/bin/
建立 socks5proxywrapper文件
在socks5proxywrapper文件中写入
```
#!/bin/sh
connect -S 127.0.0.1:7070 "$@"

配置 git

[core]
        gitproxy = /path/to/socks5proxywrapper
或者

export GIT_PROXY_COMMAND="/path/to/socks5proxywrapper"
```
