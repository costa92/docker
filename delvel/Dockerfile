FROM golang:1.20.0 AS builder 
WORKDIR /build 

# 这里他的 main.go 没有直接在项目主目录，不同于其他 golang 开源项目。
RUN git clone --depth 1 --branch v1.20.0 https://github.com/go-delve/delve.git && \
    cd /build/delve/cmd/dlv && \
    go build -o /build/delve/bin/dlv

FROM golang:1.20.0
 
COPY --from=builder /build/delve/bin/dlv /usr/local/bin/dlv