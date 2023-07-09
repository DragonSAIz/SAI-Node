# 测试脚本

## 融合怪测试

```shell
bash <(wget -qO- --no-check-certificate https://github.com/spiritLHLS/ecs/raw/main/ecs.sh)
```

## 流媒体测试

```shell
bash <(curl -L -s check.unlock.media) -M 4
```



# bbr拥堵控制算法

> 经实测,cake最优,fq和fq-p极不稳定
>
> FQ/FQ_P(激进)
>
> CAKE(均衡)
>
> 以下为玄学,具体用bbr还是其他拥堵算法未经实际调研
>
> 1、优质线路vps，可以用5.5+cake
>
> 2、劣质线路vps，即延迟过高，用bbr plus
>
> 3、电信、高峰期、劣质线路vps，即丢包严重，建议用锐速

```shell
wget --no-check-certificate -O tcpx.sh https://raw.githubusercontent.com/ylx2016/Linux-NetSpeed/master/tcpx.sh && chmod +x tcpx.sh && ./tcpx.sh
```

![image-20230424173811806](https://raw.githubusercontent.com/DragonSAIz/PicGo-img/main/image-20230424173811806.png)

之后每次运行只需要输`./tcpx.sh`即可

## 使用说明

1.确认需要使用的内核

2.安装内核后重启

3.开启拥堵算法+队列算法后重启

## 一键开启/关闭swap

```bash
wget https://www.moerats.com/usr/shell/swap.sh && bash swap.sh
```

