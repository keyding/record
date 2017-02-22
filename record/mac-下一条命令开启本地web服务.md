### Mac 下一条命令开启本地web服务

命令行进入到指定目录下，在哪个目录下执行命令，哪个目录就是根目录

	python -m SimpleHTTPServer 8080 （端口可任意指定）

访问：http://localhost:8080 (同一个局域网IP可访问)

Web服务器模块有三种：

- BaseHTTPServer   : 提供基本的Web服务和处理器类，分别是HTTPServer和BaseHTTPRequestHandler。
- SimpleHTTPServer : 包含执行GET和HEAD请求的SimpleHTTPRequestHandler类。
- CGIHTTPServer    : 包含处理POST请求和执行CGIHTTPRequestHandler类。