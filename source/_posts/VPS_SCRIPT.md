title: VPS 脚本汇总
tags:
  - VPS
  - Linux
  - Script
categories:
  - VPS
author: Blanca
date: 2022-04-24 04:57:00
---
一些vps常用的脚本集合
<!--more-->
## vps 路由测试

```bash
wget https://raw.githubusercontent.com/hijkpw/testrace/master/testrace.sh && bash testrace.sh
```

## 流媒体解锁测试

```bash
bash <(curl -sSL "https://github.com/CoiaPrant/MediaUnlock_Test/raw/main/check.sh")
```

## **测试服务器的各项参数**

```bash
wget -qO- bench.sh | bash
```

## 安装bbr

```bash
wget --no-check-certificate -O /opt/bbr.sh https://github.com/teddysun/across/raw/master/bbr.sh
chmod 755 /opt/bbr.sh
/opt/bbr.sh
```

安装完成后，脚本会提示需要重启 VPS，输入 y 并回车后重启。重启完成后，进入 VPS，验证一下是否成功安装最新内核并开启 TCP BBR，输入以下检查：

```bash
# 手动安装
# 添加下列两行到 /etc/sysctl.conf
net.core.default_qdisc=fq
net.ipv4.tcp_congestion_control=bbr
# 立即生效
sysctl -p
```

No.1

```bash
uname -r
```

查看内核版本，显示为新版内核就表示 OK 了。

No.2

```bash
sysctl net.ipv4.tcp_available_congestion_control
```

返回值一般为：

```bash
net.ipv4.tcp_available_congestion_control = bbr cubic reno
```

或者：

```bash
net.ipv4.tcp_available_congestion_control = reno cubic bbr
```

No.3

```bash
sysctl net.ipv4.tcp_congestion_control
```

返回值一般为：

```bash
net.ipv4.tcp_congestion_control = bbr
```

No.4

```bash
sysctl net.core.default_qdisc
```

返回值一般为：

```
net.core.default_qdisc = fq
```

No.5

```
lsmod | grep bbr
```

返回值有 tcp_bbr 模块即说明 bbr 已启动。比如：

```
tcp_bbr                20480  3
```