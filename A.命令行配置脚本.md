## 1.命令行配置 RouterOS

经过这段时间对 RouterOS 各类基础配置的整理，发现即使是熟练使用 Winbox 来配置，也需要消耗大量的时间。  

因此我这里整理了一份纯命令行配置 RouterOS CHR 版本的脚本，请查阅文件 [ros_shortcut_chr_pppoe_dns.conf](./src/shortcut/ros_shortcut_chr_pppoe_dns.conf) 。  

对于 RouterOS 原生硬件配置脚本，例如 RB750Gr3 ，请参考文件 [ros_shortcut_native_pppoe.conf](./src/shortcut/ros_shortcut_native_pppoe.conf) 。  

同时，基于 RB750Gr3 自带的初始化脚本（精简防火墙版本），请参考文件 [ros_shortcut_native_pppoe_simple.conf](./src/shortcut/ros_shortcut_native_pppoe_simple.conf) 。  

脚本包含了配置 RouterOS 的必要内容，其余事项在文件中有额外说明，希望能够减少大家初始化配置 RouterOS 的时间 :) 。  

## 2.配置脚本说明

所有脚本文件放置路径为 [src目录](./src) ，具体说明如下：  

|目录名称|文件名|说明|适用对象|
|--|--|--|:--:|
|[interfaces](./src/interfaces)|[ros_define_interfaces_pppoe.conf](./src/interfaces/ros_define_interfaces_pppoe.conf)|定义接口脚本，适用于 PPPoE 拨号场景|CHR / 官方硬件|
||[ros_define_interfaces_dhcp.conf](./src/interfaces/ros_define_interfaces_dhcp.conf)|定义接口脚本，适用于光猫拨号场景|CHR / 官方硬件|
|-|-|-|-|
|[firewall](./src/firewall)|[ros_blackhole_ipv4.conf](./src/firewall/ros_blackhole_ipv4.conf)|IPv4 黑洞路由脚本|CHR / 官方硬件|
||[ros_blackhole_ipv6.conf](./src/firewall/ros_blackhole_ipv6.conf)|IPv6 黑洞路由脚本|CHR / 官方硬件|
||[ros_firewall_ipv4_pppoe.conf](./src/firewall/ros_firewall_ipv4_pppoe.conf)|PPPoE 模式，IPv4 高级防火墙脚本，Fasttrack 关闭|CHR / 官方硬件|
||[ros_firewall_ipv4_pppoe_dns.conf](./src/firewall/ros_firewall_ipv4_pppoe_dns.conf)|PPPoE 模式，IPv4 高级防火墙脚本，Fasttrack 关闭，内网 DNS 服务器|CHR / 官方硬件|
||[ros_firewall_ipv4_pppoe_simple.conf](./src/firewall/ros_firewall_ipv4_pppoe_simple.conf)|PPPoE 模式，IPv4 精简防火墙脚本|CHR / 官方硬件|
||[ros_firewall_ipv4_dhcp.conf](./src/firewall/ros_firewall_ipv4_dhcp.conf)|DHCP 模式，IPv4 高级防火墙脚本|CHR / 官方硬件|
||[ros_firewall_ipv4_dhcp_dns.conf](./src/firewall/ros_firewall_ipv4_dhcp_dns.conf)|DHCP 模式，IPv4 高级防火墙脚本，内网 DNS 服务器|CHR / 官方硬件|
||[ros_firewall_ipv4_dhcp_simple.conf](./src/firewall/ros_firewall_ipv4_dhcp_simple.conf)|DHCP 模式，IPv4 精简防火墙脚本|CHR / 官方硬件|
||[ros_firewall_ipv6_pppoe.conf](./src/firewall/ros_firewall_ipv6_pppoe.conf)|IPv6 高级防火墙脚本|CHR / 官方硬件|
||[ros_firewall_ipv6_pppoe_dns.conf](./src/firewall/ros_firewall_ipv6_pppoe_dns.conf)|IPv6 高级防火墙脚本，内网 DNS 服务器|CHR / 官方硬件|
||[ros_firewall_ipv6_pppoe_simple.conf](./src/firewall/ros_firewall_ipv6_pppoe_simple.conf)|IPv6 精简防火墙脚本|CHR / 官方硬件|
|-|-|-|-|
|[qos](./src/qos)|[ros_qos_cake.conf](./src/qos/ros_qos_cake.conf)|CAKE 算法的简单队列配置脚本，要求 Fasttrack 关闭|CHR / 官方硬件|
||[ros_qos_cake_fasttrack.conf](./src/qos/ros_qos_cake_fasttrack.conf)|CAKE 算法的队列树配置脚本，可与 Fasttrack 搭配使用|CHR / 官方硬件|
|-|-|-|-|
|[schedule](./src/schedule)|[ros_schedule_script.conf](./src/schedule/ros_schedule_script.conf)|定时任务配置脚本，定时邮件推送、PPPoE 重播、系统自动升级|CHR / 官方硬件|
|-|-|-|-|
|[email](./src/email)|[ros_email_log_worker.conf](./src/email/ros_email_log_worker.conf)|日志收集邮件 推送脚本|CHR / 官方硬件|
||[ros_email_res_worker_chr.conf](./src/email/ros_email_res_worker_chr.conf)|资源状态邮件 推送脚本|CHR|
||[ros_email_res_worker_native.conf](./src/email/ros_email_res_worker_native.conf)|资源状态邮件 推送脚本|官方硬件|
|-|-|-|-|
|[upgrade](./src/upgrade)|[ros_sys_upgrade_worker_chr.conf](./src/upgrade/ros_sys_upgrade_worker_chr.conf)|系统自动更新脚本|CHR|
||[ros_sys_upgrade_worker_native.conf](./src/upgrade/ros_sys_upgrade_worker_native.conf)|系统自动更新脚本|官方硬件|
|-|-|-|-|
|[shortcut](./src/shortcut)|[ros_official_init_script.conf](./src/shortcut/ros_official_init_script.conf)|官方硬件自带的初始化脚本，仅供研究|官方硬件|
||[ros_shortcut_chr_pppoe.conf](./src/shortcut/ros_shortcut_chr_pppoe.conf)| CHR 配置脚本，高级防火墙、CAKE QoS、邮件推送、额外日志存储等|CHR|
||[ros_shortcut_chr_pppoe_dns.conf](./src/shortcut/ros_shortcut_chr_pppoe_dns.conf)|与 CHR 脚本类似，内网 DNS 服务器|CHR|
||[ros_shortcut_native_pppoe.conf](./src/shortcut/ros_shortcut_native_pppoe.conf)|与 CHR 脚本类似，但根据官方硬件做了部分适配修改，使用 Fq_Codel QoS |官方硬件|
||[ros_shortcut_native_pppoe_simple.conf](./src/shortcut/ros_shortcut_native_pppoe_simple.conf)|与官方硬件脚本类似，但根据硬件性能使用精简防火墙并移除了 QoS |官方硬件|
||[ros_shortcut_native_dhcp.conf](./src/shortcut/ros_shortcut_native_dhcp.conf)|使用 DHCP 模式联网，高级防火墙，暂不支持配置 IPv6 |官方硬件|
||[ros_shortcut_native_dhcp_simple.conf](./src/shortcut/ros_shortcut_native_dhcp_simple.conf)|与 DHCP 脚本类似，精简防火墙，移除了 QoS |官方硬件|
