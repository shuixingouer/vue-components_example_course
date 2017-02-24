#组件的创建和注册：
 1. Vue.extend()是Vue构造器的扩展，调用Vue.extend()创建的是一个组件构造器。
 2. Vue.extend()构造器有一个选项对象，选项对象的template属性用于定义组件要渲染的HTML。
 3. 使用Vue.component()注册组件时，需要提供2个参数，第1个参数时组件的标签，第2个参数是组件构造器。
 4. 组件应该挂载到某个Vue实例下，否则它不会生效。

#全局注册和局部注册
 调用Vue.component()注册组件时，组件的注册是全局的，这意味着该组件可以在任意Vue示例下使用。
 如果不需要全局注册，或者是让组件使用在其它组件内，可以用选项对象的components属性实现局部注册。

#父组件和子组件
 子组件只能在父组件的template中使用。
 以子标签的形式在父组件中使用是错误的。
 在父组件标签外使用子组件也是错误的。

#组件注册语法糖
 var vm2 = new Vue({
     el: '#app2',
     components: {
         // 局部注册，my-component2是标签名称
         'my-component2': {
             template: '<div>This is the second component!</div>'
         },
         // 局部注册，my-component3是标签名称
         'my-component3': {
             template: '<div>This is the third component!</div>'
         }
     }
 })

#使用script或template标签
 使用<script>标签时，type指定为text/x-template，意在告诉浏览器这不是一段js脚本，浏览器在解析HTML文档时会忽略<script>标签内定义的内容。
 <script type="text/x-template" id="myComponent">
     <div>This is a component!</div>
 </script>

 如果使用<template>标签，则不需要指定type属性。

#组件的el和data选项
 在定义组件的选项时，data和el选项必须使用函数。
 Vue.component('my-component', {
     data: function(){
         return {a : 1}
     }
 })

#使用props
 组件实例的作用域是孤立的。这意味着不能并且不应该在子组件的模板内直接引用父组件的数据。可以使用 props 把数据传给子组件。
 由于HTML特性不区分大小写，camelCase的prop用于特性时，需要转为 kebab-case（短横线隔开）。例如，在prop中定义的myName，在用作特性时需要转换为my-name。
 <child-component v-bind:子组件prop="父组件数据属性"></child-component>

#prop的绑定类型
 prop默认是单向绑定：当父组件的属性变化时，将传导给子组件，但是反过来不会。这是为了防止子组件无意修改了父组件的状态
 可以使用.sync显式地指定双向绑定，这使得子组件的数据修改会回传给父组件。
 可以使用.once显式地指定单次绑定，单次绑定在建立之后不会同步之后的变化，这意味着即使父组件修改了数据，也不会传导给子组件。

#prop验证

#filterBy过滤器



博文地址：http://www.cnblogs.com/keepfool/p/5625583.html









