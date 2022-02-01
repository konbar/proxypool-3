# proxypool

> 自动抓取 Telegram 频道、订阅地址、公开互联网上的 Shadowsocks、ShadowsocksR、VMess 和 Trojan 节点信息，聚合去重检测后提供节点列表

This project is based on [Sansui233/proxypool](https://github.com/Sansui233/proxypool) modified.

该项目基于 [Sansui233/proxypool](https://github.com/Sansui233/proxypool) 修改。

## Usage

podman, buildah and skopeo are recommended, if you use Arch Linux, execute:

推荐使用 podman、buildah 和 skopeo，如果你使用 Arch Linux，请执行：

```
# pacman -S podman podman-compose buildah skopeo
```

The following is a simple execute example:

下面是一个简单的执行样例：

```
$ git clone https://github.com/qculug/proxypool.git
$ cd proxypool
$ buildah build -t proxypool
```

```yml
version: "3"

services:
  proxypool:
    image: localhost/proxypool:latest
    container_name: proxypool
    restart: always
    volumes:
      - ./config.yaml:/home/proxypool/config.yaml
      - ./config:/home/proxypool/config

networks:
  default:
    external: true
    name: nginx_https_default
```

```
$ podman-compose up -d
```
