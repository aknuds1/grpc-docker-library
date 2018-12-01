# Dockerfile for gRPC Go
FROM golang:1.11

RUN apt-get update && apt-get -y install unzip && apt-get clean

# install protobuf
ENV PB_VER 3.6.1
ENV PB_URL https://github.com/google/protobuf/releases/download/v${PB_VER}/protoc-${PB_VER}-linux-x86_64.zip
RUN mkdir -p /tmp/protoc && \
    curl -L ${PB_URL} > /tmp/protoc/protoc.zip && \
    cd /tmp/protoc && \
    unzip protoc.zip && \
    cp /tmp/protoc/bin/protoc /usr/local/bin && \
    cp -R /tmp/protoc/include/* /usr/local/include && \
    chmod go+rx /usr/local/bin/protoc && \
    cd /tmp && \
    rm -r /tmp/protoc

# Get the grpc-go source from GitHub
ENV GO_GRPC_VER 1.16.0
RUN mkdir -p /tmp/grpc-go && \
    curl -L https://github.com/grpc/grpc-go/archive/v${GO_GRPC_VER}.zip > /tmp/grpc-go/grpc-go.zip && \
    cd /tmp/grpc-go && \
    unzip grpc-go.zip && \
    mkdir -p /go/src/google.golang.org/grpc/ && \
    cp -r /tmp/grpc-go/grpc-go-${GO_GRPC_VER}/* /go/src/google.golang.org/grpc/

# Install protoc-gen-go
ENV GO_PROTOBUF_VER 1.2.0
RUN mkdir -p /tmp/protobuf && \
    curl -L https://github.com/golang/protobuf/archive/v${GO_PROTOBUF_VER}.zip > /tmp/protobuf/protobuf.zip && \
    cd /tmp/protobuf && \
    unzip protobuf.zip && \
    mkdir -p /go/src/github.com/golang/protobuf/ && \
    cp -r /tmp/protobuf/protobuf-${GO_PROTOBUF_VER}/* /go/src/github.com/golang/protobuf/ && \
    go install github.com/golang/protobuf/protoc-gen-go
