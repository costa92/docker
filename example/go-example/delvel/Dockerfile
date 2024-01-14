FROM golang:1.20.0 AS builder

ENV GO111MODULE=on \
    GOPROXY=https://goproxy.cn,direct \
    GIN_MODE=release
ENV CGO_ENABLED 0
ENV GOOS linux
# 将代码复制到构建镜像中。

WORKDIR /workspace
COPY . .
RUN go mod download
RUN --mount=type=cache,target=/go

RUN go build -gcflags "all=-N -l" -o demo
RUN ls -l && cd /workspace && ls -l

# Path: Dockerfile
FROM costa92/go-base-debug:v1.0.0
WORKDIR /app
COPY --from=builder /workspace/demo /app/demo
EXPOSE 8080
ENTRYPOINT ["/app/demo"]
