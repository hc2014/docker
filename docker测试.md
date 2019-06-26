1. 新建一个.net core项目 添加docker支持，项目默认名字为  WebApplication1

2. docker  for window客户端 点击 “Switch to Linux Containers”

3. 右键docker  for window客户端，setting->Daemon->Registry 输入“https://registry.docker-cn.com”  然后 Apply ,docker 重启

4. 在项目目录下面 docker 编译项目

   ````c#
   docker build  -t web_test -f .\WebApplication1\Dockerfile .
   ````

   然后 查看 一下当前已经存在的镜像

   ```
   docker images
   ```

5. 然后启动一个应用

   ```
   docker run -d -p 8800:80 --name web1 web_test
   ```

   这个命令的意思是 以**web_test**镜像启动一个项目， 把容器**8800端口映射到物理机上面的80端口** 并且应用的名字是 web1

6. 启动应用

   ```
   docker start web1
   ```

   打开浏览器 http://localhost:8800

7. 可以同时启动多个应用

   ```
   docker run -d -p 8801:80 --name web2 web_test
   docker run -d -p 8802:80 --name web3 web_test
   ```

8. 停止、删除应用

   ```
   docker stop 应用id(docker ps 查看)
   docker rm -f web1
   ```

   

