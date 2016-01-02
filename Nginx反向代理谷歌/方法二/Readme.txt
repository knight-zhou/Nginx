直接代理谷歌域名
但是有可能被墙的风险

生成密钥的时候：
要注意的是，在中间会叫你填一大堆东西，唯一一个重要的是 Common Name，这个写上你的域名，要不然有的浏览器会不认。

openssl genrsa -des3 -out server.key 2048
openssl rsa -in server.key -out server.key  # 这是生成没有密码的证书，你刚开始要输入一个四位以上的密码
openssl req -new -key server.key -out server.csr
openssl x509 -req -days 3650 -in server.csr -signkey server.key -out server.crt


########################
注意：

ngx_http_sub_module模块是一个过滤器，它修改网站响应内容中的字符串，比如你想把响应内容中的‘iuwai’全部替换成‘aaaaa‘，
这个模块已经内置在nginx中，但是默认未安装，需要安装需要加上配置参数：–with-http_sub_module

subs_filter 是第三方模块，可以多重替换

nginx -V如下：
