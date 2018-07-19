<template>
    <div>
      <slot-body>this is slot body</slot-body>
      <div>
         <slot-base><template slot="header"><h1>this is title</h1></template>
         <p>this is content</p>
         <p>this another content</p>
         <template slot="footer"><p>this is footer</p></template>
        </slot-base>
      </div>
      <div>
        <slot-button></slot-button>
        <slot-button><slot>this is button</slot></slot-button>
      </div>

      <div>
        <slot-scope><slot>data is {{user.name}}</slot></slot-scope>
      </div>

      <div>
        <h3>这里是父组件</h3>
        <slot-list>
              <span v-for="item in user.data">数据是: {{ item }} </span>
        </slot-list>
      </div>
    </div>
</template>

<script>
import Vue from 'vue'
export default{
  data () {
    return {
      user: {
        name: 'this is name',
        data: ['zhangsan', 'lisi', 'wanwu', 'zhaoliu', 'tianqi', 'xiaoba']
      }
    }
  }
}
// 插槽内容
Vue.component('slot-body', {
  template: '<span><slot></slot></span>'
})
// 具名插槽
Vue.component('slot-base', {
  template: '<span><header><slot name="header"></slot></header><main><slot></slot></main><footer><slot name="footer">' +
  '</slot></footer></span>'
})
// 默认插槽
Vue.component('slot-button', {
  template: '<button type="submit"><slot>Submit</slot></button>'
})
// 编译作用域
// 父组件模板的所有东西都会在父级作用域内编译，子组件模板的所有东西都会再子级作用域内编译
Vue.component('slot-scope', {
  template: '<span><slot></slot></span>'
})
Vue.component('slot-list', {
  template: '<div><h3>这里是子组件<slot></slot></h3></div>'
})
</script>
