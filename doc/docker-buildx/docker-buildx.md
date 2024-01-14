# docker buildx

## 常用命令

1. 查看版本

```sh
docker buildx version
```

2. 查看有哪些可用架构
```sh
 docker buildx inspect --bootstrap
```

3. 接下来，我們建立一个 builder 并使用（初次安裝执行一次即可）
   
```sh
docker buildx create --use
```
4. 建立 builder

```sh
docker buildx create --name mybuilder
```
5. 使用 builder

```sh
docker buildx use mybuilder
```

6. 查看 builder 列表

```sh
docker buildx ls
```

7. 构建命令

使用docker build 

```sh
docker build . -t MY_ACCOUNT/IMAGE_NAME:latest
```

可以使用下面命令替换

```sh
docker buildx build --load -t MY_ACCOUNT/IMAGE_NAME:latest --platform linux/amd64 .
```

上面代码效果二者一样

8. 清除缓存命令

```sh
docker buildx prune
```
9. 停止 builder 命令
```sh
docker buildx builder_name
```