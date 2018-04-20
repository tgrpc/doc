Verify Resp
==============

gRpc返回内容可以格式化为json数据，然后验证json数据的kv。

json数据解析包：[`github.com/toukii/jsnm`](https://github.com/toukii/jsnm)


### json resp 的写法:

 - 1 key以`,`分隔，不要写多余的空格

 - 2 如果是数组下标，直接写数字，如 `0` `1` `2` `3`; 如果map的key是数字，则用`""`引起来，如 `"0"`

 - 3 value 可以支持 string, int64, float64, string 数组, float64 数组; int{32,64}的数组要写成float64的数组。

 ```toml
string: '{"msg":"success"}'
int64: 999
float64: 999.0
string 数组: ['{"msg":"success"}', '{"msg":"fail"}']
int32 数组: [999.0, 999.0]
int64 数组: [999.0, 999.0]
float64 数组: [999.0, 998.0]
 ```
