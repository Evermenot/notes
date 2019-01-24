#### Github + Hexo自定义博客搭建

> 1. 准备：Github账号（略~.~）、配置环境（windows环境下）
>
>    ```javascript
>    /* 配置环境：
>         1. 安装Node（作用：生成静态页面）
>         2. 安装Git（作用：提交本地的hexo到github上去）
>         3. 配置SSHKeys（作用：不用每次提交代码的时候都输入账号密码，可以省略，配置SSH自己百度o.o）
>    ```
>
> 2. 安装Hexo
>
>    ```javascript
>    /* 1. 创建文件夹（如：blog存放hexo配置文件）
>       2. 在上一步新建的文件夹下安装Hexo
>       3. npm install -g hexo
>       4. hexo init（初始化）
>       5. hexo generate/g（作用：生成静态页面至public目录下）
>       6. hexo server（作用：启动服务）
>       测试：http://localhost:4000
>    ```
>
> 3. 配置Github
>
>    ```javascript
>    /* 1. 创建仓库Repository
>    	    注：仓库名*必须*为userName.github.io，如：我的为Evermenot.gitHub.io
>       2. 建立关联
>       		使用_config.yml文件建立关联命令：vim _config.yml
>       3. 在文件末尾添加
>       		deploy；
>       			type: git
>       			repository: https://github.com/Evermenot/Evermenot.github.io.git
>       			branch: master
>       	4. 部署
>       	     npm install --save hexo-deployer-git （安装部署模块）
>       	     执行部署的配置命令：hexo deploy   
>       	     测试：在浏览器中输入http://Evermenot.github.io即可
>         5. 后期每次维护常使用以下三条命令
>       	   hexo clean
>       	   hexo generate
>       	   hexo deploy 
>    ```
>
> 4. 自定义域名
>
>    ```javascript
>    /* 假定上面的步骤都已成功
>       1. 申请域名（如：阿里旗下的万网，以下也以万网为例）
>       2. 在 github设置Settings中,找到Custom domain将申请的域名填写上去保存
>       
>       3. 在万网的域名解析部分
>       	  3.1 添加域名解析 （https://pages.github.com/做下面的custom Url 有介绍）
>       	  记录类型：IPV4地址 主机记录：@  解析路线：默认   记录值：192.30.252.154/192.30.252.153（该iP地址是由GitHub提供的，两个可以都配置）
>       	  添加一个CNAME，主机记录写@，记录值：http://xxxx.github.io
>          3.2 在该仓库项目里添加CNAME文件（无后缀名）  文件内容为 你申请的域名
>          
>       注: 域名前不要加www, 加上www的为二级域名
>    ```
>
>    ​