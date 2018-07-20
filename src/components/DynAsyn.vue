<template xmlns:v-on="http://www.w3.org/1999/xhtml" xmlns:v-bind="http://www.w3.org/1999/xhtml">
  <div>
      <div>动态组件</div>
      <div>
        <button v-for="tab in tabs" v-bind:key="tab" v-on:click="currentTab = tab">{{ tab }}</button>
        <component  v-bind:is="currentTabComponent"></component>
      </div>
    <div>
      <div>keep-alive</div>
      <div>
        <button v-for="tab in tabs" v-bind:key="tab" v-on:click="currentTab = tab">{{ tab }}</button>
        <keep-alive>
          <component  v-bind:is="currentTabComponent"></component>
        </keep-alive>
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
      tabs: ['Home', 'Posts']
    }
  },
  computed: {
    currentTabComponent: function () {
      return 'tab-' + this.currentTab.toLowerCase()
    }
  }
}
Vue.component('blog-post', {
  props: ['title'],
  template: '<h3>{{ title }}</h3>'
})
// 组件切换
Vue.component('tab-tab1', {
  template: '<div>tab1</div>'
})
Vue.component('tab-tab2', {
  template: '<div>tab2</div>'
})
Vue.component('tab-tab3', {
  template: '<div>tab3</div>'
})
Vue.component('tab-home', {
  data () {
    return {
      currentTab: 'tab1',
      listTabs: ['tab1', 'tab2', 'tab3']
    }
  },
  computed: {
    currentTabComponent: function () {
      return 'tab-' + this.currentTab.toLowerCase()
    }
  },
  template: '<div><span v-for="listTab in listTabs" v-bind:key="listTab" v-on:click="currentTab=listTab">{{ listTab }}' +
  '</span><component v-bind:is="currentTabComponent"></component></div>'
})
Vue.component('tab-posts', {
  template: '<div>Posts component</div>'
})
</script>
