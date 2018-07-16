<template>
  <div>
    <div>{{number+1}}</div>
    <div>{{ok?'yes':'no'}}</div>
    <div>{{message.split(' ').reverse().join(' ')}}</div>
    <div v-if="seen">you can see me</div>
    <div v-if="!seen">you can't seen me</div>
    <div><a v-bind:href="url">百度一下</a></div>
    <button v-on:click="numberAdd()">hi</button>
  </div>
</template>

<script>
  export default{
    data(){
      return {
        number: 6,
        ok: true,
        message: 'this is grammer message',
        seen: true,
        url: "https://www.baidu.com",
      }
    },
    methods: {
      numberAdd:function () {
        console.log('hello')
      }
    }
  }
</script>
