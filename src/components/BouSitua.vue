<template>
    <div>
      <div>
        <parent-component></parent-component>
      </div>
      <template>
        <div>
          <h3>我是父组件</h3>
          <input v-model="parentMsg">
          <p>{{parentMsg}}</p>
          <child-component></child-component>
        </div>
      </template>
      <template>
        <div>
          <h3>我是子组件</h3>
          <p>{{msg}}</p>
          <button v-on:click="showData">显示父组件数据</button>
        </div>
      </template>
    </div>
</template>

<script>
import Vue from 'vue'
export default{
  data: function () {
    return {
      rootData: 'hello world'
    }
  }
}
// 访问根实例
Vue.component('parent-component', {
  data () {
    return {
      parentMsg:'我是父组件的数据'
    }
  },
  components: {
    'child-component': {
      data () {
        return {
          msg: ''
        }
      },
      methods: {
        showData() {
          this.msg = this.$root.parentMsg;
        }
      }
    }
  }
})
</script>
