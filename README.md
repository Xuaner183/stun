## OpenWrt的STUN扩展（包含 `stund`和 `stun-client`）

*复刻自[awe1p/stun: support stun in openwrt](https://github.com/awe1p/stun)*

编译
----

```bash
# 进入OpenWrt源代码目录
# 克隆本仓库
git clone https://github.com/awe1p/stun.git package/network/stun
# 配置：选择 Network → stun-client 和 Network → stund
make menuconfig
# 编译
make V=s
```

使用
----

```
# 需要至少两台路由器分别作为服务端和客户端
# 在具有两个互联网连接接口的STUN服务端运行
stund -v
# 在STUN客户端运行以检测NAT类型
stun-client {服务器IP} -v
#例如：
stun-client stun.miwifi.com -v
```

结果解读
--------

```
你将得到
Independent Mapping, Independent Filter = 全锥型NAT（NAT1）
Independent Mapping, Address Dependent Filter = 受限锥型NAT（NAT2）
Independent Mapping, Port Dependent Filter = 端口受限锥型NAT（NAT3）
Dependent Mapping = 对称型NAT（NAT4）
```
