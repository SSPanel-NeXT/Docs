## 可配置选项一览

```json
{
    //通用
    "offset_port_user": "", //前端/订阅中下发的端口
    "offset_port_node": "", //节点服务器下发的端口
    "server_user": "", //前端/订阅中下发的服务器地址
    "host": "", //SNI
	//Shadowsocks
        "mu_encryption": "chacha20-ietf-poly1305" // 加密方式
	"plugin": "", //SIP002插件
	"plugin_option": "", //插件参数
    //V2Ray
    "v2_port": "",
    "tls": "0",
    "enable_vless": "0",
    "alter_id": "",
    "network": "",
    "security": "",
	"encryption":"",
    "path": "",
    "verify_cert": "true",
    "obfs":"",
    "header": {
        "type": "http",
        "request": {},
        "response": {}
    },
    //Trojan
    "trojan_port": "",
    "allow_insecure": "0",
    "grpc": "0",
    "servicename": "",
    "enable_xtls": "",
    "flow": "",
	//Trojan-Go
	"mux": "0",
	"transport": "none",
	"transport_plugin": "",
	"transport_method": "",
	//Clash 相关，仅用于 Clash 通用订阅，不影响节点配置下发
	//参考文档 https://github.com/Dreamacro/clash/wiki/configuration
	"plugin-opts": {
        // 对应 Clash yaml 文件中 plugin-opts 的配置
    },
	"ws-opts": {
        // 对应 Clash yaml 文件中 ws-opts 的配置
    },
	"h2-opts": {
        // 对应 Clash yaml 文件中 h2-opts 的配置
    },
	"http-opts": {
        // 对应 Clash yaml 文件中 http-opts 的配置
    },
	"grpc-opts": {
        // 对应 Clash yaml 文件中 grpc-opts 的配置
    }
}
```

# V2ray

## tcp示例

``` json
{
	"offset_port_node": "12345",
	"server_sub": "hk.domain.com",
	"alter_id": "0",
	"network": "tcp",
	"security": "none",
}
```

## tcp+http示例

```json
{
	"offset_port_node": "12345",
	"server_sub": "hk.domain.com",
	"alter_id": "0",
	"network": "tcp",
	"security": "none",
	"header": {
        "type": "http",
        "request": {
            "path": ["/"],
  			"headers": {
    			"Host": ["www.baidu.com"]
            }
        },
        "response": {}
    }
}
```

## tcp+tls示例

```json
{
	"offset_port_node": "443",
	"server_sub": "hk.domain.com",
	"host": "hk.domain.com",
	"alter_id": "0",
	"network": "tcp",
	"security": "tls",
}
```

## ws示例

```json
{
	"offset_port_node": "80",
	"server_sub": "hk.domain.com",
	"host": "hk.domain.com",
	"alter_id": "0",
	"network": "ws",
	"security": "none",
	"path": "/v2ray"
}
```

## ws+tls示例

```json
{
	"offset_port_node": "443",
	"server_sub": "hk.domain.com",
	"host": "hk.domain.com",
	"alter_id": "0",
	"network": "ws",
	"security": "tls",
	"path": "/v2ray"
}
```

## grpc+tls示例

```json
{
	"offset_port_node": "443",
	"server_sub": "hk.domain.com",
	"host": "hk.domain.com",
	"alter_id": "0",
	"network": "grpc",
	"security": "tls",
	"servicename": "some_name"
}
```

## 中转端口示例
在任一配置中设置 `offset_port_user` 为用户连接端口

``` json
{
	"offset_port_user": "8888",
	"offset_port_node": "12345",
	"server_sub": "hk.domain.com",
	"alter_id": "0",
	"network": "tcp",
	"security": "none",
}
```

此时用户连接端口为8888，节点监听端口为12345

## 启用vless
在任一配置中设置 `enable_vless: 1` 为用户连接端口

``` json
{
	"offset_port_node": "443",
	"server_sub": "hk.domain.com",
	"host": "hk.domain.com",
	"alter_id": "0",
	"network": "tcp",
	"security": "tls",
	"enable_vless": "1"
}
```
请开启vless同时务必使用tls或者xtls。

## 启用xtls
在任一配置中设置 `security: xtls`。

``` json
{
	"offset_port_node": "443",
	"server_sub": "hk.domain.com",
	"host": "hk.domain.com",
	"alter_id": "0",
	"network": "tcp",
	"security": "xtls",
	"enable_vless": "1"
}
```

# Trojan

## tcp示例

``` json
{
	"offset_port_node": "443",
	"server_sub": "hk.domain.com",
	"host": "hk.domain.com"
}
```

## grpc示例

``` json
{
	"offset_port_node": "443",
	"server_sub": "hk.domain.com",
	"host": "hk.domain.com",
	"grpc": "1",
	"servicename": "some_name"
}
```

## 中转示例
在任一配置中设置 `offset_port_user` 为用户连接端口
``` json
{
	"offset_port_user": "443",
	"offset_port_node": "12345",
	"server_sub": "hk.domain.com",
	"host": "hk.domain.com"
}
```
此时用户连接443，节点监听12345

## 启用xtls

在任一配置中设置 `enable_xtls: 1`。

``` json
{
	"offset_port_node": "443",
	"server_sub": "hk.domain.com",
	"host": "hk.domain.com",
	"enable_xtls": "1"
}
```
