> 1. 注册全局组件必须在Vue实例之前（通常指vm之前），**是为了保证注册的全局组件在任意的实例中都可以使用**
>
> 2. Vue.component(参数一，参数二)，参数一为要注册的**全局组件的名称**，参数二的类型可以为一个**对象**还可以为一个**构造函数**
>
> 3. Vue.extend 扩展 实例 构造器（个人理解就是创建简化了的vm，一般用来创建全局组件）
>
>    ```js
>    // 1.创建一个特殊的vue实例
>            const com1 = Vue.extend({
>                template: '<h2>vue的全局组件--定义方式一--略略略略略略</h2>',
>                data: function () {
>                    // 扩展实例中的data必须是一个函数
>                    return {}
>                }
>            })
>            console.dir(com1);    // 可以看出创建的com1为构造函数 而非组件   它上面的原型属性prototype指向  Vue$3 {constructor: ƒ}
>    ```
>
> 4. 组件中的data必须是函数   实质是解决多个组件间共用一个data对象    
>
> 5. 使用驼峰命名的组件  在以自定义标签的形式写入到容器中时，必须使用小写且连接部分使用‘-’来连接
>
> 6. **父组件向子组件传值**
>
>    > 简述： 使用v-blind指令在组件标签中绑定自定义属性，属性值为父组件data中要传递给子组件的数据，同时用子组件的props属性来接收（注：props为数组类型，数组中的每一项为组件标签中绑定的自定义属性名的字符串）
>    >
>    > ```javascript
>    > <div id='app'>
>    >         <com1 v-bind:sub-msg="fatherMsg"></com1>
>    >         <!-- 错误写法<com1 v-bind:subMsg="fatherMsg"></com1> -->
>    >     </div>
>    >     <script>
>    >         var vm = new Vue({
>    >             el: '#app',
>    >             data: {
>    >                 fatherMsg: 'wa我是父组件 传给子组件的 数据 资产'
>    >             },
>    >             methods: {},
>    >             components: {
>    >                 //定义私有组件
>    >                 'com1': {
>    >                     template: `<h2>子组件中的标题:{{ subMsg }}</h2>`,
>    >                     props: ['subMsg']
>    >                 }
>    >             }
>    >         });
>    >     </script>
>    > ```
>    >
>    > ```javascript
>    > // 向子组件传递function
>    > <template id="tmpl">
>    >         // 添加点击事件触发子组件methods中的方法
>    >         <input type="button" value="子组件按钮--哦" @click='btnClick'>
>    >     </template>
>    >     <div id='app'>
>    >         // 添加自定义事件  来触发父组件methods中的show方法
>    >         <com1 @func1='show'></com1>
>    >     </div>
>    >
>    >     <script src='./lib/vue-2.5.9.js'></script>
>    >     <script>
>    >         var vm = new Vue({
>    >             el: '#app',
>    >             data: {},
>    >             methods: {
>    >                 show() {
>    >                     console.log('成功 调用父组件的show方法')
>    >                 }
>    >             },
>    >             components: {
>    >                 'com1': {
>    >                     template: '#tmpl',
>    >                     methods: {
>    >                         btnClick() {
>    >                             //通过在UI模板中调用btnClick方法触发父组件传递过来的自定义事件
>    >                             this.$emit('func1')
>    >                         }
>    >                     }
>    >                 }
>    >             }
>    >         });
>    > ```
>    >
>
>    ​
>
> 7. 子组件向父组件传值**
>
>    > 简述: 使用v-on在子组件名的标签中添加自定义事件，并在子组件的methods中添加一个方法并在函数体中使用this.$emit('标签中自定义事件名'，‘子组件要传递的参数’)   参考上面的父组件向子组件传递function例子   \$emit的第二个参数使用父组件的方法的形参来接收并进行数据操作
>    >
>    > ```javascript
>    >         var vm = new Vue({
>    >             el: '#app',
>    >             data: {
>    >                 msgFromSon: ''
>    >             },
>    >             methods: {
>    >                 show(args) {
>    >                     this.msgFromSon = args;
>    >                     console.log(this.msgFromSon)
>    >                 }
>    >             },
>    >             components: {
>    >                 'com1': {
>    >                     template: '#tmpl',
>    >                     data: function () {
>    >                         return {
>    >                             subMsg: '成功传递子组件中的数据'
>    >                         }
>    >                     },
>    >                     methods: {
>    >                         btnClick() {
>    >                             this.$emit('func1',this.subMsg)
>    >                         }
>    >                     }
>    >                 }
>    >             }
>    >         });
>    > ```
>    >
>
> 8. vue中的ref和$refs
>
>    > 简述: ref是用来给子组件添加引用信息。而$refs对象就是用来储存这些引用信息的（方便开发者来操作DOM）（在普通的DOM上使用，引用指向DOM元素；在子组件上使用，引用指向组件实例，个人感觉其整体功能类似于js中的DOM节点选择器）
>    >
>    > https://www.cnblogs.com/xumqfaith/p/7743387.html
>
>
> 9. es5和es6导入导出
>
>    > es5的引入也就是导入使用的是require(),es6中使用import...from...来实现导入
>    >
>    > es5的导出使用的是module.exports(),es6中使用export default
>    > 上面的导入导出功能为成对出现，不能混用
>
> 10. webpack的基本使用
>
>     > 1. 首先创建项目  `npm init` （生成package.json文件，记录了项目的基本信息）
>     >
>     > 2. 安装webpack `npm install webpack --save-dev`既要在项目本地安装，全局也要安装 目的是在全局使用webpack命令    `其实如果不全局安装webpack那么在使用webpack命令时就要将webpack在node_module中的全部路径在命令行中加上，如：./node_modules/webpack`
>     >
>     > 3. 新建webpack.config.js配置文件      dos命令 type nul>webpack.config.js
>     >
>     >    创建完配置文件，在配置文件中导入‘path’模块 再在module.exports中配置打包的入口及出口，最后在控制台输入 webpack  --config  webpack.config.js   生成bundle.js即表示成功
>     >
>     >    ```javascript
>     >    // webpack.config.js  文件基本配置
>     >    // 引入模块
>     >    const path = require('path');
>     >
>     >    // 导出
>     >    module.exports = {
>     >        entry: path.join(__dirname, './src/main.js'),
>     >        output: {
>     >            path: path.join(__dirname, './dist'),  // 输出文件名的路径
>     >            filename: 'bundle,js'      // 打包输出文件名
>     >        },
>     >        plugins: [],  // 相关插件的配置    如：html-webpack-plugin 要创建插件实例
>     >        module: {}    // 相关加载器的配置  如：less-loader     要配置加载器的规则
>     >    }
>     >    ```
>     >
>     >    ​
> 







