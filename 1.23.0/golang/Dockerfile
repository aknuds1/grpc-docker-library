# Dockerfile for gRPC Go
FROM golang:1.12-alpine3.10

RUN apk --no-cache add unzip curl git protobuf build-base

# Get the grpc-go source from GitHub
ENV GRPC_GO_VER 1.23.0
RUN mkdir -p /tmp/grpc-go && \
  curl -L https://github.com/grpc/grpc-go/archive/v${GRPC_GO_VER}.zip > /tmp/grpc-go/grpc-go.zip && \
  cd /tmp/grpc-go && \
  unzip grpc-go.zip && \
  mkdir -p /go/src/google.golang.org/grpc/ && \
  cp -r /tmp/grpc-go/grpc-go-${GRPC_GO_VER}/* /go/src/google.golang.org/grpc/

# Install protoc-gen-go
ENV GO_PROTOBUF_VER 1.3.2
RUN mkdir -p /tmp/protobuf && \
  curl -L https://github.com/golang/protobuf/archive/v${GO_PROTOBUF_VER}.zip > /tmp/protobuf/protobuf.zip && \
  cd /tmp/protobuf && \
  unzip protobuf.zip && \
  mkdir -p /go/src/github.com/golang/protobuf/ && \
  cp -r /tmp/protobuf/protobuf-${GO_PROTOBUF_VER}/* /go/src/github.com/golang/protobuf/ && \
  go install github.com/golang/protobuf/protoc-gen-go
