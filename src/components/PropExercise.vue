<template>
    <div>
    <blog-post post-title="hello"></blog-post>
    <blog-title v-bind:title="post.title"></blog-title>
    <blog-title v-bind:title="post.title+ ' by '+post.author.name"></blog-title>
    <blog-num v-bind:num="20"></blog-num>
    <blog-num v-bind:num="post.likes"></blog-num>
    <blog-bool bool></blog-bool>
    <blog-bool v-bind:bool="false"></blog-bool>
    <blog-bool v-bind:bool="post.isPublished"></blog-bool>
    <blog-arr v-bind:arr="[3, 4, 5]"></blog-arr>
    <blog-arr v-bind:arr="post.commentIds"></blog-arr>
    <blog-str v-bind:str="{name:'veronica',company:'veridian dynamics'}"></blog-str>
    <blog-str v-bind:str="post.author "></blog-str>
    <blog-str v-bind:str="post "></blog-str>
    <blog-check v-bind:title="post.title"></blog-check>
    </div>
</template>

<script>
import Vue from 'vue'
export default{
  data: function () {
    return {
      post: {
        title: 'this is title',
        author: {
          name: 'this is name'
        },
        likes: 520,
        isPublished: true,
        commentIds: [9, 8, 7, 6, 5]
      }
    }
  }
}
// 使用DOM中的模板时，驼峰命名法的prop名需要使用其等价的短横线分割命名法命名
Vue.component('blog-post', {
  props: ['postTitle'],
  template: '<h3>{{postTitle}}</h3>'
})
// 传递静态或动态prop
Vue.component('blog-title', {
  props: ['title'],
  template: '<h3>{{title}}</h3>'
})
// 传递一个数字
Vue.component('blog-num', {
  props: ['num'],
  template: '<h3>{{num}}</h3>'
})
// 传递一个布尔值
Vue.component('blog-bool', {
  props: ['bool'],
  template: '<h3>{{bool}}</h3>'
})
// 传递一个数组
Vue.component('blog-arr', {
  props: ['arr'],
  template: '<h3>{{arr}}</h3>'
})
// 传递一个对象
Vue.component('blog-str', {
  props: ['str'],
  template: '<h3>{{str}}</h3>'
})
// prop验证
Vue.component('blog-check', {
  props: {
    // title: Number,
    title: String
  },
  template: '<h3>{{title}}</h3>'
})
</script>
