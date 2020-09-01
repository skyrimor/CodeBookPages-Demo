# Vue 规范

### 目录结构

```javascript
   src                               源码目录
|-- api                              接口，统一管理
|-- assets                           静态资源，统一管理
|-- components                       公用组件，全局文件
|    |   |-- StaffWorkbench           组件模块名
|    |   |-- |-- index.vue            
|-- filters                          过滤器，全局工具
|-- icons                            图标，全局资源
|-- datas                            模拟数据，临时存放
|-- lib                              外部引用的插件存放及修改文件
|-- mock                             模拟接口，临时存放
|-- router                           路由，统一管理
|-- store                            vuex, 统一管理
|-- views                         视图目录
|   |-- staffWorkbench               视图模块名
|   |-- |-- staffWorkbench.vue       模块入口页面
|   |-- |-- indexComponents          模块页面级组件文件夹
```

### vue 文件基本结构

```javascript
<template>
    <div>
    <!--必须在div中编写页面-->
    </div>
</template>
<script>
    export default {
components : {
},
    data () {
        return {
        }
    },
        mounted() {
        }，
        methods: {
        }
}
</script>
<!--声明语言，并且添加scoped-->
<style lang="scss" scoped>
</style>
```

### 多个特性的元素规范

多个特性的元素应该分多行撰写，每个特性一行。(增强更易读)

```javascript
<!-- bad -->
<img src="https://vuejs.org/images/logo.png" alt="Vue Logo">
<my-component foo="a" bar="b" baz="c"></my-component>

<!-- good -->
<img
src="https://vuejs.org/images/logo.png"
alt="Vue Logo"
>
<my-component
foo="a"
bar="b"
baz="c"
>
</my-component>
```

### 元素特性的顺序

原生属性放前面，指令放后面

```javascript
  - class
  - id,ref
  - name
  - data-*
  - src, for, type, href,value,max-length,max,min,pattern
  - title, alt，placeholder
  - aria-*, role
  - required,readonly,disabled
  - is
  - v-for
  - key
  - v-if
  - v-else-if
  - v-else
  - v-show
  - v-cloak
  - v-pre
  - v-once
  - v-model
  - v-bind,:
  - v-on,@
  - v-html
  - v-text
```

### 组件选项顺序

```javascript
  - components
  - props
  - data
  - computed
  - created
  - mounted
  - metods
  - filter
  - watch
```

### 为组件样式设置作用域

```javascript
<template>
<button class="button button-close">X</button>
</template>



<style scoped>
.button {
border: none;
border-radius: 2px;
}

.button-close {
background-color: red;
}
</style>
```

## 注释规范

### 务必添加注释列表

- 公共组件使用说明

- 各组件中重要函数或者类说明

- 复杂的业务逻辑处理说明

- 特殊情况的代码处理说明,对于代码中特殊用途的变量、存在临界值、函数中使用的 hack、使用了某种算法或思路等需要进行注释描述

- 多重 if 判断语句

- 注释块必须以

  ```javascript
  /**（至少两个星号）开头**/
  ```

- 单行注释使用//

### 单行注释

注释单独一行，不要在代码后的同一行内加注释。例如：

```javascript
bad

var name =”abc”; // 姓名    

good

// 姓名
var name = “abc”; 
```

### 多行注释

组件使用说明，和调用说明

```javascript
    /**
    * 组件名称
    * @module 组件存放位置
    * @desc 组件描述
    * @author 组件作者
    * @date 2017年12月05日17:22:43
    * @param {Object} [title]    - 参数说明
    * @param {String} [columns] - 参数说明
    * @example 调用示例
    *  <hbTable :title="title" :columns="columns" :tableData="tableData"></hbTable>
    **/
```