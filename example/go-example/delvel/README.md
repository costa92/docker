# go 运行 debug配置

## 安装 dlv

利用 golang 安装命令

```sh
 go install github.com/go-delve/delve/cmd/dlv@latest
```

## 编译住代码

```sh
go build -gcflags "all=-N -l" -o demo
```

## 服务运行编译代码

```sh
 dlv --listen=:2345 --headless=true --api-version=2 --accept-multiclient exec ./demo
```

## dlv 连接
```sh
dlv connect ip:2345
```