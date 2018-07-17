<template>
    <div>
      <div>
        <button-counter></button-counter>
        <div>组件复用</div>
        <button-counter></button-counter>
        <button-counter></button-counter>
      </div>
      <div>通过props向子组件传递数据</div>
      <blog-post title="this is vue title1"></blog-post>
      <blog-post title="this is vue title2"></blog-post>
      <blog-post title="this is vue title3"></blog-post>
      <div>
        <div>动态组件</div>
        <div id="dynamic-component-demo" class="demo">
          <button
            v-for="tab in tabs"
            v-bind:key="tab"
            v-bind:class="['tab-button', { active: currentTab === tab }]"
            v-on:click="currentTab = tab"
          >{{ tab }}</button>

          <component
            v-bind:is="currentTabComponent"
            class="tab"
          ></component>
        </div>
      </div>
    </div>
</template>

<script>
import Vue from 'vue'
export default{
  // 动态组件数据
  data () {
    return {
      currentTab: 'Home',
      tabs: ['Home', 'Posts', 'Archive']
    }
  },
  computed: {
    currentTabComponent: function () {
      return 'tab-' + this.currentTab.toLowerCase()
    }
  }
}

Vue.component('button-counter', {
  // data必须是一个函数,因此每个实例可以维护一份被返回对象的独立的拷贝
  data: function () {
    return {count: 0}
  },
  template: '<button v-on:click="count++">you click me {{count}}</button>'
})
Vue.component('blog-post', {
  props: ['title'],
  template: '<h3>{{ title }}</h3>'
})
// 组件切换
Vue.component('tab-home', {
  template: '<div>Home component</div>'
})
Vue.component('tab-posts', {
  template: '<div>Posts component</div>'
})
Vue.component('tab-archive', {
  template: '<div>Archive component</div>'
})
</script>
