grpc 自动化测试
==============

## 1. run server

开启gRpc服务，参考[github.com/tgrpc/ngrpc](https://github.com/tgrpc/ngrpc)


## 2. tgrpc

```
go get github.com/tgrpc/tgrpc/tg ## get tgrpc tool
tg -i ## init config
tg -c tgrpc.toml ## run tgrpc
```
[tgrpc config说明](tgrpc-config.md)

[resp的验证规则](verify.md)

[reinvoke规则](reinvoke.md)

### prototool

[prototool 示例](example.md)
