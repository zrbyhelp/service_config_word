### 用于处理跨域问题
>通过docker将远程地址代理成本地地址端口  
> 当前路径控制台运行`docker-compose up`开始直接运行使用  
> 运行之后本文件`nginx.conf`会与虚拟机文件链接,如需修改直接修改本文件该文件即可

> 相关配置说明  
> 代码更新:  
> 1. `docker-compose down`关闭现有服务
> 2. `docker-compose up -d`更新并后台运行
> 
> 端口映射配置:  
> 1. `docker-compose.yml`文件ports字段可将本地端口映射到虚拟机多以配置多个,前面为本地端口地址,后面为虚拟机地址
> 2. `nginx.conf`文件内stream对象下可以映射多个远程地址
> 3. 每次修改之后需要更新
