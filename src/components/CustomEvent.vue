<template>
    <div>
      <base-checkbox v-model="lovingVue"></base-checkbox>
      <span>{{lovingVue}}</span>
      <div>
        <button @click="add">button</button>
        <button-event @click="cut"></button-event>
        <button-event @click.native="cut"></button-event>
        <span>{{count}}</span>
      </div>
      <div>
        <span>:foo.sync="bar" 实际就是 :foo="bar" @update:foo="val => bar = val" 的语法糖</span>
        <div>父组件bar: {{bar}}</div>
        <comp :foo.sync="bar"></comp>
      </div>
    </div>
</template>

<script>
import Vue from 'vue'
export default{
  data () {
    return {
      checked: false,
      lovingVue: '',
      count: 0,
      bar: 0
    }
  },
  methods: {
    add () {
      this.count++
    },
    cut () {
      this.count--
    }
  }
}
// 自定义组件的 v-model
Vue.component('base-checkbox', {
  model: {
    prop: 'checked',
    event: 'change'
  },
  props: {
    checked: Boolean
  },
  template: `
    <input
      type="checkbox"
      v-bind:checked="checked"
      v-on:change="$emit('change', $event.target.checked)"
    >
  `
})
// 将原生事件绑定到组件
Vue.component('button-event', {
  template: '<button>button-even</button>'
})
// .sync修饰符
Vue.component('comp', {
  template: '<div><button @click="increment">点我更新子组件foo++</button><div>子组件foo: {{foo}}</div></div>',
  props: ['foo'],
  methods: {
    increment: function () {
      this.foo++
      this.$emit('update:foo', this.foo)
    }
  }
})
</script>
