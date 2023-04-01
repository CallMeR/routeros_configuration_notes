# RouterOS 折腾手记

## 介绍
RouterOS 路由器的安装以及折腾手记。

- RouterOS 适用版本：7.8 Stable


- 演示机：
    - 虚拟化：Proxmox VE
    - CPU：host
    - 内存：2GB
    - 网卡：VirtIO
    - SCSI 控制器：VirtIO SCSI Single

- 外部网络：
    - 光猫：桥接模式
    - RouterOS：`PPPoE`

- 内部网络：
    - IPv4 网络
        - IP 地址：`172.16.1.1`
        - 子网掩码：`255.255.255.0` ( 即 `/24` )
        - 网关：`172.16.1.1`
        - 内网 DNS：`172.16.1.2` , `172.16.1.3`
    - IPv6 网络
        - 分配方式：`SLAAC`
        - GUA 前缀：`Prefix Delegation`
        - ULA 前缀：`fdac::/64`
        - ULA 地址：`fdac::1`
        - 内网 DNS：`fdac::2` , `fdac::3`


### 系列章节

0.  [PVE下RouterOS安装](./00.PVE下RouterOS安装.md)
1.  [定义网络接口和基础配置](./01.定义网络接口和基础配置.md)
2.  [配置防火墙和流量整形](./02.配置防火墙和流量整形.md)
3.  [RouterOS正版系统激活](./03.RouterOS正版系统激活.md)
4.  [系统参数调整](./04.系统参数调整.md)
5.  [系统自动化及邮件脚本](./05.系统自动化及邮件脚本.md)
6.  [RouterOS使用内网DNS服务器](./06.RouterOS使用内网DNS服务器.md)
7.  [DHCP静态地址和Options配置](./07.DHCP静态地址和Options配置.md)
8.  [使用附加硬盘记录系统日志](./08.使用附加硬盘记录系统日志.md)
9.  [RouterOS配置IPv6](./09.RouterOS配置IPv6.md)

### 附录

A.  [RouterOS命令行配置脚本.md](./A.RouterOS命令行配置脚本.md)

### 文章说明

1.  本系列文章涉及的部分参数需要手动调整来符合切实使用需求。
2.  随着 RouterOS 系统的迭代更新，截图中的内容和实际页面显示可能存在差异。
3.  如需引用，请注明本文出处。
