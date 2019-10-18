## 签名

```
md5(k1v1k2v2...knvn59a1469a1469a1461214a9bf269a14).upcase()
```

请求的参数除 sign 外所有 key 和 value 按照参数的首字母顺序排列，以 key1+value+key2+value....的方式拼接在一起，然后再追加 secret_token=59a1469a1469a1461214a9bf269a14），然后转成 utf-8 编码，接着进行 md5 加密，最后全部转大写即可。

