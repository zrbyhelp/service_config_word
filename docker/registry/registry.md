## 私有化镜像容器
> 用于本地镜像上传云服务器并私有化
### 配置
> 1.优先安装docker,步骤参见`docker安装篇`  
> 2.`sudo docker pull registry`下载registry镜像  
### 加密
> 1.`sudo apt-get install apache2-utils`安装Apache的htpasswd
> 2.`sudo htpasswd -Bbn  账号 密码 > 秘钥路径` 指定文件下生成htpasswd文件
### 运行
> 1.```sudo docker run -d -p 本地端口:5000 
> -v 本地映射路径:/tmp/registry 
> -v 秘钥路径:/auth
> -e "REGISTRY_AUTH_HTPASSWD_REALM=Registry Realm" 
> -e "REGISTRY_AUTH_HTPASSWD_PATH=/auth/htpasswd"
> -e "REGISTRY_AUTH=htpasswd"
> --privileged=true registry```运行镜像
### 查看镜像列表
> 列表:`curl -X GET http://映射地址/v2/_catalog -u 账号:密码`  
> 详情:`curl -X GET http://映射地址/v2/familykitchen-app/tags/list -u 账号:密码`  
## 镜像上传
> 将新镜像修改为符合私服规范的Tag:  
> `docker tag 镜像名:版本 服务器地址/镜像名:版本`   
> 修改docker配置以支持http:(文件在客户端设置内可以找到docker engine,加入以下语句)
> ```yaml
> "insecure-registries": [
>     "192.168.0.101:5001"
>  ]
> ```
> 上传:`docker push -t 符合私服规范的Tag的镜像名称或ID:版本号`
> 下载:`docker pull Registry的网络映射:Registry的端口映射/私有库中的镜像名字:版本号`
