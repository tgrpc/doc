reinvoke
==============

next invoke的参数，可以通过上次直接结果获取。

使用@开头的单词，不包含特殊符号，只允许出现`,` `""`, 支持map，slice及map与slice组合的json解析。

示例：

```
{"name":"@Go!","value":["@value","100.0"]}
```

数据为:
```
{"Go":"golang","value":0.0}
```

得到的结果是：

```
{"name":"golang!","value":["0.0","100.0"]}
```