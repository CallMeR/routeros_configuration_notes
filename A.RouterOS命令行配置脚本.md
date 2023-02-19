## 1.命令行配置RouterOS

经过这段时间对 RouterOS 各类基础配置的整理，发现即使是熟练使用 Winbox 来配置，也需要消耗大量的时间。  

因此我这里整理了一份纯命令行配置 RouterOS CHR 版本的脚本，请查阅文件 [fox_ros_chr_shortcut.conf](./src/shortcut/fox_ros_chr_shortcut.conf) 。  

对于 RouterOS 原生硬件配置脚本，例如 RB750Gr3 ，请参考文件 [fox_ros_native_shortcut.conf](./src/shortcut/fox_ros_native_shortcut.conf) 。  

同时，基于 RB750Gr3 自带的初始化脚本（精简防火墙版本），请参考文件 [fox_ros_rb750gr3_simple_shortcut.conf](./src/shortcut/fox_ros_rb750gr3_simple_shortcut.conf) 。  

脚本包含了配置 RouterOS 的必要内容，其余事项在文件中有额外说明，希望能够减少大家初始化配置 RouterOS 的时间 :) 。  

## 2.配置脚本说明

所有脚本文件放置路径为 [src目录](./src) ，具体说明如下：  

|目录名称|文件名|说明|适用对象|
|--|--|--|:--:|
|[interfaces](./src/interfaces)|[fox_ros_define_interfaces.conf](./src/interfaces/fox_ros_define_interfaces.conf)|RouterOS 定义接口脚本，适用于 PPPoE 拨号场景|CHR / 官方硬件|
|-|-|-|-|
|[firewall](./src/firewall)|[fox_ros_firewall_ipv4.conf](./src/firewall/fox_ros_firewall_ipv4.conf)|RouterOS IPv4 高级防火墙脚本，Fasttrack 关闭|CHR / 官方硬件|
||[fox_ros_firewall_ipv6.conf](./src/firewall/fox_ros_firewall_ipv6.conf)|RouterOS IPv6 高级防火墙脚本|CHR / 官方硬件|
|-|-|-|-|
|[qos](./src/qos)|[fox_ros_qos_cake.conf](./src/qos/fox_ros_qos_cake.conf)|RouterOS 使用 CAKE 算法的简单队列配置脚本，要求 Fasttrack 关闭|CHR / 官方硬件|
||[fox_ros_qos_cake_fasttrack.conf](./src/qos/fox_ros_qos_cake_fasttrack.conf)|RouterOS 使用 CAKE 算法的队列树配置脚本，可与 Fasttrack 搭配使用|CHR / 官方硬件|
|-|-|-|-|
|[schedule](./src/schedule)|[fox_ros_schedule_script.conf](./src/schedule/fox_ros_schedule_script.conf)|RouterOS 定时任务配置脚本，定时邮件推送、PPPoE 重播、系统自动升级|CHR / 官方硬件|
|-|-|-|-|
|[email](./src/email)|[fox_ros_email_log_worker.conf](./src/email/fox_ros_email_log_worker.conf)|RouterOS 日志收集邮件 推送脚本|CHR / 官方硬件|
||[fox_ros_email_res_worker.conf](./src/email/fox_ros_email_res_worker.conf)|RouterOS 资源状态邮件 推送脚本|CHR|
||[fox_ros_native_email_res_worker.conf](./src/email/fox_ros_native_email_res_worker.conf)|RouterOS 资源状态邮件 推送脚本|官方硬件|
|-|-|-|-|
|[upgrade](./src/upgrade)|[fox_ros_chr_sys_upgrade_worker.conf](./src/upgrade/fox_ros_chr_sys_upgrade_worker.conf)|RouterOS 系统自动更新脚本|CHR|
||[fox_ros_native_sys_upgrade_worker.conf](./src/upgrade/fox_ros_native_sys_upgrade_worker.conf)|RouterOS 系统自动更新脚本|官方硬件|
|-|-|-|-|
|[shortcut](./src/shortcut)|[fox_ros_native_init_script.conf](./src/shortcut/fox_ros_native_init_script.conf)|RouterOS 官方硬件自带的初始化脚本，仅供研究|官方硬件|
||[fox_ros_chr_shortcut.conf](./src/shortcut/fox_ros_chr_shortcut.conf)|RouterOS CHR 命令行配置脚本，包含高级防火墙、内网 DNS、CAKE QoS、邮件推送、额外日志存储等|CHR|
||[fox_ros_native_shortcut.conf](./src/shortcut/fox_ros_native_shortcut.conf)|与 CHR 脚本类似，但根据官方硬件做了部分适配修改，使用 Fq_Codel QoS|高性能官方硬件|
||[fox_ros_rb750gr3_simple_shortcut.conf](./src/shortcut/fox_ros_rb750gr3_simple_shortcut.conf)|与高性能官方硬件脚本类似，但根据硬件性能使用精简防火墙并移除了QoS|官方硬件|
