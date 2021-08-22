一、通过命令配置

1. 命令

```bash
npm config set registry https://registry.npm.taobao.org
```

2. 验证命令

```bash
npm config get registry
```

如果返回https://registry.npm.taobao.org，说明镜像配置成功。

二、通过使用cnpm安装

1. 安装cnpm

```bash
npm install -g cnpm --registry=https://registry.npm.taobao.org
```

2. 使用cnpm

```bash
cnpm install xxx
```