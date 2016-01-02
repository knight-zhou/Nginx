直接代理谷歌域名
但是有可能被墙的风险

生成密钥的时候：
要注意的是，在中间会叫你填一大堆东西，唯一一个重要的是 Common Name，这个写上你的域名，要不然有的浏览器会不认。

openssl genrsa -des3 -out server.key 2048
openssl rsa -in server.key -out server.key  # 这是生成没有密码的证书，你刚开始要输入一个四位以上的密码
openssl req -new -key server.key -out server.csr
openssl x509 -req -days 3650 -in server.csr -signkey server.key -out server.crt


########################
以后再也不百度技术问题了，都是抄来抄去，而且细节问题还抄错.
subs_filter  居然写出sub_filter 

nginx -V如下：
nginx version: nginx/1.7.8
built by gcc 4.4.7 20120313 (Red Hat 4.4.7-16) (GCC) 
TLS SNI support enabled
configure arguments: --prefix=/usr/local/nginx --with-pcre=../pcre-8.38 --with-openssl=../openssl-1.0.1j --with-zlib=../zlib-1.2.8 --with-http_ssl_module --add-module=../ngx_http_google_filter_module --add-module=../ngx_http_substitutions_filter_module/


