# tgrpc config

以示例程序 [github.com/tgprc/ngrpc](https://github.com/tgprc/ngrpc)的 LangService为例，配置文件如下：

```toml
log_level = "debug"
[service]
[service.lang]
  address = "localhost:2080"
  reuse_desc = false
  proto_base_path = "$GOPATH/src/github.com/tgrpc/ngrpc"
  include_imports = "helloworld/lang.proto"
  keepalive = "100s"

[[invokes]]
service = "lang"
method = "helloworld.LangService/List"
headers = ["customerId:123", "region:UK"]
data = '{}'
n = 1
interval = "200ms"
[invokes.resp]
  cost = "2ms"
  [invokes.resp.json]
    'langs,0,birthday' = 1136185445.0
    totalCount = 999.0
    'langs,1,versions,0,id' = 700.0
    'langs,1,versions,0,vi32s,0' = 111.0
    'langs,1,versions,0,vi32s' = [111.0,222.0]
    'langs,1,versions,0,vi64s,0' = 111.0
    'langs,1,versions,0,vi64s' = [111.0,222.0]
    'langs,1,versions,0,vf64s,0' = 111.0
    'langs,1,versions,0,vf64s' = [111.0,222.0]
    'langs,1,versions,0,vstrs,0' = 'str1'
    'langs,1,versions,0,vstrs' = ['str1','str2']
[invokes.then]
service = "lang"
method = "helloworld.LangService/GetLang"
headers = ["customerId:123", "region:UK"]
data = '{"name":"Golang"}'
n = 1
```

## config

 - log_level 日志级别

 - tgprc.reuse_desc 是否重用proto descriptor 文件

 - tgrpc.proto_base_path proto文件位置

 - tgrpc.include_imports 当前要执行的服务proto文件

 - invokes.service 所调的服务别名

 - invokes.method 所调服务的方法

 - invokes.headers 所服务方法的header，通过metadata传递，kv形式，以`=`连接

 - invokes.data 所调服务方法的参数，json格式

 - invokes.n 调用服务该方法`n`次

 - invokes.interval 调用服务该方法`n`次, 间歇时间：interval, 写法：`1s`, `10ms`, 不写：0ms(并发执行)

 - invokes.resp.cost 方法预估最大耗时，超时会给出错误提示。

 - invokes.resp.json 参考 [verify](verify.md)
