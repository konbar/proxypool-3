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

Please go to the qcurug/dockerfiles repository, proxypool is packaged and published on ghcr.io.

请前往 qculug/dockerfiles 仓库，proxypool 已打包并发布于 ghcr.io。

```
$ podman run --rm -it ghcr.io/qculug/proxypool:latest
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
