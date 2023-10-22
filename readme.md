<!--
 Copyright (C) 2023 wwhai

 This program is free software: you can redistribute it and/or modify
 it under the terms of the GNU Affero General Public License as
 published by the Free Software Foundation, either version 3 of the
 License, or (at your option) any later version.

 This program is distributed in the hope that it will be useful,
 but WITHOUT ANY WARRANTY; without even the implied warranty of
 MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 GNU Affero General Public License for more details.

 You should have received a copy of the GNU Affero General Public License
 along with this program.  If not, see <http://www.gnu.org/licenses/>.
-->

# RPC解码器示例
这是一个 RULEX 的 RPC 解码器 golang 服务模板，用来开发私有设备接入。
## 生成
```sh

export GOROOT=/usr/local/go
export GOPATH=$HOME/go
export GOBIN=$GOPATH/bin
export PATH=$PATH:$GOROOT:$GOPATH:$GOBIN
# Install protoc
go get -u google.golang.org/grpc
go install google.golang.org/protobuf/cmd/protoc-gen-go@latest
go install google.golang.org/grpc/cmd/protoc-gen-go-grpc@latest

protoc -I ./ --go_out ./ --go_opt paths=source_relative \
    --go-grpc_out=./ --go-grpc_opt paths=source_relative \
    ./trailer.proto

```

## 构建
```sh
go build
```
## 示例
```lua
    function(data)
        print(rpc:Request('grpcCodec001', "cmd", "arg"))
        return true, data
    end
```
## 社区
- wwhai