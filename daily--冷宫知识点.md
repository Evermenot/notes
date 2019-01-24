## 冷宫知识点

> ##### 1. 模块的异步加载
>
> ```javascript
> /*
> 1. 原因：模块的异步加载（防止Dom渲染过慢）
>
> 2. <script src="js/require.js" defer async="true" ></script>
>    注： 上面标签里的async属性表明这个文件需要异步加载，避免网页失去响应。IE不支持这个属性，只支持defer，所以把defer也写上。
>  
> 3. <script src="js/require.js" data-main="js/main"></script>
>    注： data-main属性的作用是，指定网页程序的主模块。在上例中，就是js目录下面的main.js，这个文件会第一个被require.js加载。由于require.js默认的文件后缀名是js，所以可以把main.js简写成main。
> ```
>
> 相关文章: http://www.ruanyifeng.com/blog/2015/05/require.html阮一峰博客
>
> 
>
> ###### 2.DOS下创建文件   挺有意思.....
>
> ```javascript
> /*
> 1.创建文件夹 
>    md [盘符:\][路径\]新目录名   如：md c:\test\myfolder 
>    没写盘符及路径默认在当前路径下创建  `mkdir 文件夹名`也可创建 
>    md的全称：make directory
>
> 2.删除文件夹
>    'rd或rmdir'  '/s /q [盘符:\][路径\]新目录名' 
>    rd只能删除空文件夹 加上'/s'即可直接删除非空文件夹
>    rd在删除文件夹时会提示是否确定删除 加上'/q'即quiet 无需提示直接删除
>    
> 3.创建文件
>    type nul>'文件名' 创建一个空文件
>    'echo' '要添加内容'>'文件名'
> 4.删除文件
>    del '文件名'
> ```
>
> ##### 3.web性能调试优化（达）
>
> ```javascript
> /* 前端优化经验  可以了解下 
>    1. performance.timing     查看页面耗时
>    2. h5获取电池电量Api       (没记住、前端可以获取用户手机电量针对性的做出一些优化)
>    3. 多普乐测速      可以获取DNS解析时间、用户带宽
>    4. link标签预解析DNS		<link rel="dns-prefetch">
>    5. 域名收敛    将域名都收敛到服务器域名下
>    6. 页面加载速度工具：Google pagespeed  (会给出页面要优化的点)
>    7. 远程调试工具：web inspector remote
> ```
>
> 



