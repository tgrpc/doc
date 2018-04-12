# grpc测试

req body 通过json传入，Metadata通过header传入。

简单示例：

```
echo '{"name":"toukii"}' | prototool -H "abc:123" grpc helloworld 0.0.0.0:50051 helloworld.Greeter/SayHello -
```
