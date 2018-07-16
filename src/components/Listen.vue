<template>
  <!--计算属性-->
  <div>
    <div>Original message:"{{message}}"</div>
    <div>Computed reversed message1:"{{reversedMessage1}}"</div>
    <div>Computed reversed message2:"{{reversedMessage2()}}"</div>
    <div>{{fullName}}</div>
  </div>
</template>

<script>
  export default{
    data(){
      return {
        //计算属性数据
        message: 'hello',
        firstName: 'Foo',
        lastName: 'Bar',
      }
    },

    computed: {
      //计算属性是基于它们的依赖进行缓存的，计算属性只有在它的相关依赖发生变化时才会重新求值，只要message没有发生改变，就不必重新执行函数
      reversedMessage1: function () {
        return this.message.split('').reverse().join('')
      },
      fullName: function () {
        return this.firstName + ' ' + this.lastName
      }
    },

    methods: {
      //每当重新渲染时，调用方法总会再次执行函数，在不希望产生缓存的条件下，可以优先考虑方法
      reversedMessage2: function () {
        return this.message.split('').reverse().join('')
      },
    }
  }
</script>
