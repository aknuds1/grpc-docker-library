# Dockerfile for gRPC Go
FROM golang:1.14-alpine3.11

RUN apk --no-cache add unzip curl git protobuf build-base

# Get the grpc-go source from GitHub
ENV GRPC_GO_VER 1.29.1
RUN mkdir -p /tmp/grpc-go && \
  curl -L https://github.com/grpc/grpc-go/archive/v${GRPC_GO_VER}.zip > /tmp/grpc-go/grpc-go.zip && \
  cd /tmp/grpc-go && \
  unzip grpc-go.zip && \
  mkdir -p /go/src/google.golang.org/grpc/ && \
  cp -r /tmp/grpc-go/grpc-go-${GRPC_GO_VER}/* /go/src/google.golang.org/grpc/

# Install protoc-gen-go
ENV GO_PROTOBUF_VER 1.4.2
RUN GO111MODULE=on go get -u github.com/golang/protobuf/protoc-gen-go@v${GO_PROTOBUF_VER}
