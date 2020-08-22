# 一、Vue框架是什么，有什么特点，怎么用

## 1.vue是渐进式Javascript框架

### 什么是渐进式

### 渐进式框架的大概意思就是你可以只用我的一部分，而不是用了我这一点就必须用我的所有部分。

## 2.vue的特点

#### 1.遵循MVVM模式（m->model(数据对象)  v->view(视图) vm->view model）

#### 2.编码简洁，体积小，运行效率高，适合移动端/PC端

#### 3.它本身只关注UI，可以轻松引入Vue插件或其他第三方库开发项目

#### 4.vue插件

​     vue-cli:Vue脚手架    

​      vue-resource(axios):ajax请求

​      vue-router:路由

​       vuex:状态管理

​       vue-lazyload:图片懒加载

​       vue-scroller:页面滑动相关

​        mint-ui:基于Vue的UI组件库（移动端）

​        element-ui:基于Vue的UI组件库（PC端）

## 3.编写Vue代码步骤

#### 1.引入Vue.js

##### ` <script src='vue.js'></script>`

#### 2.创建Vue对象

``` <!DOCTYPE html>
<html lang="en">
```

<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
  <div id="app">
      <ul>
          <li v-for="(value,key) in Person">{{key}} :{{value}}</li>
      </ul>
      <hr/>
      <div>
          <ul>
              <li v-for="book in books">{{book}}</li>
          </ul>
          <h3>Total Price:{{totalPrice}}</h3>

      </div>
  </div>



  <script src="vue.js"></script>
  <script>
      const app=new Vue({
          el:"#app",
          data:{
              Person:{
                  name:"pussy lover",
                  age:32,
                  height:1.8,
                  measure:"36-24-36"
              },
              books:[
                  {"name":"c++programming",price:35},
                  {"name":"c#programming",price:45},
                  {"name":"java programming",price:25},
                  {"name":"Python programming",price:55}
              ]
          },

          computed:{
              totalPrice() {
                  let sum=0;
                  for(let i=0;i<this.books.length;i++){
                      sum+=this.books[i].price;
                  }
                  return sum;
              }
          }
      });
  </script>
</body>
</html> ```

<font color=red>注意:</font>

> > <font color='red'>以上用法是在没有安装webpack 和vue cli 时使用。安装了vue cli后就不要这样子使用，而且要使用组件化和模块化的开发方式</font>
> >
> > 

#### 3.安装webpack 和vue cli

1)使用这些都需要node的支持，使用要下载安装node

https://nodejs.org/en/

2）安装webpack

```bash
npm install --save-dev webpack
# 或指定版本
npm install --save-dev webpack@<version>
```

如果你使用 webpack v4+ 版本，你还需要安装 [CLI](https://webpack.docschina.org/api/cli/)。

```bash
npm install --save-dev webpack-cli
```

3）安装vue cli

Vue CLI 的包名称由 `vue-cli` 改成了 `@vue/cli`。 如果你已经全局安装了旧版本的 `vue-cli` (1.x 或 2.x)，你需要先通过 `npm uninstall vue-cli -g` 或 `yarn global remove vue-cli` 卸载它。

Node 版本要求

Vue CLI 需要 [Node.js](https://nodejs.org/) 8.9 或更高版本 (推荐 8.11.0+)。你可以使用 [nvm](https://github.com/creationix/nvm) 或 [nvm-windows](https://github.com/coreybutler/nvm-windows) 在同一台电脑中管理多个 Node 版本。

可以使用下列任一命令安装这个新的包：

```bash
npm install -g @vue/cli
# OR
yarn global add @vue/cli
```

你还可以用这个命令来检查其版本是否正确：

```bash
vue --version
```

​        

Vue CLI >= 3 和旧版使用了相同的 vue 命令，所以 Vue CLI 2 (vue-cli) 被覆盖了。
但是Vue CLI >= 3新的版本中取消了init功能，用的是create。
如果你仍然需要使用旧版本的 vue init 功能，你可以全局安装一个桥接工具：

```bash
npm install -g @vue/cli-init
```



<font color='yellow'>vue cli 2 创建项目：vue init webpack 项目名称</font>

<font color='yellow'>vue cli 3 创建项目：vue create 项目名称</font>

## vue常用属性

+ ### v-if

+ ### v-show

+ ### v-for

+ ### v-band

+ ### v-text

+ ### v-html

+ ### v-cloak

+ ### v-model 双向绑定数据 

  
## 二、用法实例

**v-cloak:**防止页面加载时，出现vue.js的变量名

用法：

```html
<div v-cloak>



 



  {{ message }}



 



</div>



 
```

***\*CSS\****

```
 
[v-cloak] {



display: none!important;



}
```

 

***\*！\*******\*important\****:能够覆盖样式原本的权重，增加指定的样式的权重

 

v-bind:属性=”js语句”，将元素节点属性的特性和变量名保持一致

1、v-bind可以简写为一个‘’：”

如：

**代码：**

```html
<body>



<div id="app">



    <h2 :title="msg"></h2>



    <p >{{msg}}</p>



 



</div>



<script>



   var vm =  new Vue({



       el: '#app',



       data:{



           msg:'养老院智能服务系统'



       }



   })



</script>



</body>



 
```

**运行结果：**

![img](https://img-blog.csdnimg.cn/20190308212931843.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3h4dG50,size_16,color_FFFFFF,t_70)

v-text=””可以与{{}}替换使用

1、v-text没有vue因网速过慢导致加载的问题

2、{{}}前后可以加值，而v-text会覆盖元素中原来的内容

3、{{}}和v-text不能识别html语言,需要使用html

**代码：**

```html
<body>



<div id="app">



    <h2 v-text="msg"></h2>



    <p >{{msg}}</p>



 



</div>



<script>



   var vm =  new Vue({



       el: '#app',



       data:{



           msg:'养老院智能服务系统'



       }



   })



</script>



</body>
```

**运行结果：**

![img](https://img-blog.csdnimg.cn/2019030821294260.png)

 

v-html指令添加html元素

**代码：**

```html
<body>



<div id="app">



    <h2 v-html="msg"></h2>



    <p >{{msg}}</p>



 



</div>



<script>



   var vm =  new Vue({



       el: '#app',



       data:{



           msg:'<h2 style="color: maroon">养老院智能服务系统</h2>'



       }



   })



</script>



</body>



 
```

**运行结果：**

![img](https://img-blog.csdnimg.cn/20190308212959159.png)

 

v-on:绑定事件

常用事件：click/mouseover/mouseup/

**代码：**

```html
<body>



<div id="app">



    <h2 v-html="msg"></h2>



    <input type="button" value="点击报名" id="submit" v-on:click="result">



 



</div>



<script>



   var vm =  new Vue({



       el: '#app',



       data:{



           msg:'<h2 style="color: maroon">养老院智能服务系统</h2>'



       },



       methods:{



           result:function(){



               alert('报名成功')



           }



       }



 



   })



</script>



</body>
```

 

**运行结果：**

![img](https://img-blog.csdnimg.cn/20190308213013223.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3h4dG50,size_16,color_FFFFFF,t_70)



  