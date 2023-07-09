# 准备工作

## 一、端口映射

一般面板都有个 `nat vps` 端口映射管理页面，不同面板有所不通，但大同小异。点击添加规则，先要映射一个 `22` 端口来连接 ssh 用，这是必要的

内网端口填写 `22`，公网端口随意填写一个 `大于10000` 的端口，并且没有被占用的（如果被占用了应该会有提示），可以直接忽略 `65432`等端口，基本都被占了，协议使用 `TCP`

（当然，有可能店家直接默认就给分配了一个 `22` 端口的映射，那么就不需要创建 `22` 端口映射了）

### 1. 查询ip

```bash
curl ifconfig.me
```

## 二、更新及安装组件

### 1. bash命令

```bash
apt update -y          # Debian/Ubuntu 命令
apt install -y curl    # Debian/Ubuntu 命令
apt install wget
```

```bash
yum update -y          # CentOS 命令
yum install -y curl    # CentOS 命令
```
### 2. `Centos`关闭防火墙

查看防火墙状态

```bash
firewall-cmd --state
```

停止 firewall

```bash
systemctl stop firewalld.service
```

禁止 firewall 开机启动

```bash
systemctl disable firewalld.service 
```

## 三、更改时区

```bash
timedatectl		# 查看当前时区
timedatectl list-timezones | grep -i shang		# 查找上海时区
sudo timedatectl set-timezone Asia/Shanghai		# 设置时区为上海
```

## 四、更改DNS

> 修改优先级 3>2>1

### 1. HOST 本地DNS解析

```bash
vi /etc/hosts
```

添加规则 例如:

```bash
1.1.1.1 www.baidu.com
```

### 2. 网卡配置文件DNS服务地址

```bash
vi /etc/sysconfig/network-scripts/ifcfg-eth0
```

添加规则 例如:

```
DSN1='1.1.1.1'
```

### 3. 系统默认DNS配置

```bash
vi /etc/resolv.conf
```

添加规则 例如:

```bash
nameserver 1.1.1.1
```

# 安装x-ui

```bash
原版
bash <(curl -Ls https://raw.githubusercontent.com/vaxilu/x-ui/master/install.sh)
```
```bash
tg bot版
bash <(curl -Ls https://raw.githubusercontent.com/FranzKafkaYu/x-ui/master/install.sh)
```

```
面板设置
用户名:
密码:
端口:
```

登录面板 `ip:端口`

添加`vmess+ws`节点

转发则用`任意门`

# 开启bbr or bbr plus

## 一、 开启自带`bbr`加速

```bash
echo "net.core.default_qdisc=fq" >> /etc/sysctl.conf
```
```bash
echo "net.ipv4.tcp_congestion_control=bbr" >> /etc/sysctl.conf
```
```bash
sysctl -p
```
```bash
lsmod | grep bbr
```

## 二、 开启 bbr plus （四合一脚本，推荐使用 bbr ，不支持 ovz ）

```bash
wget -N --no-check-certificate "https://raw.githubusercontent.com/chiakge/Linux-NetSpeed/master/tcp.sh" && chmod +x tcp.sh && ./tcp.sh
```

##  三、为 openvz 开启 bbr

详见此处[OpenVZ/LXC架构VPS开启BBR加速](https://bobqu.cyou/2020/11/25/43.html)

# 部署 tg bot

使用该脚本部署x-ui，可在x-ui面板进行bot设置

```bash
bash <(curl -Ls https://raw.githubusercontent.com/FranzKafkaYu/x-ui/master/install.sh)
```