<template>
  <div>
    <!-- v-if -->
    <div v-if="true">Yes</div>
    <div v-if="false">No</div>
    <div>
      <span v-if="ok">you can see</span>
      <span v-else>no</span>
    </div>
    <div>
      <span v-if="no">you can see</span>
      <span v-else>no</span>
    </div>
    <!-- v-else-if -->
    <div>
      <span v-if="type==='A'">A</span>
      <span v-else-if="type==='B'">B</span>
      <span v-else-if="type==='C'">C</span>
      <span v-else>not A/B/C</span>
    </div>
    <div>
      <span v-if="type1==='A'">A</span>
      <span v-else-if="type1==='B'">B</span>
      <span v-else-if="type1==='C'">C</span>
      <span v-else>not A/B/C</span>
    </div>
    <!-- 用key管理可复用的元素 -->
    <div v-if="loginType==='username'">
      <label>Username</label>
      <input placeholder="Enter your username">
    </div>
    <div v-else>
      <label>Email</label>
      <input placeholder="Enter your email address">
    </div>
    <button v-on:click="toggleType()">toggle login type</button>
    <!--添加key每次切换时，输入框都将被重新渲染-->
    <div v-if="loginType==='username'">
      <label>Username</label>
      <input placeholder="Enter your username" key="username-input">
    </div>
    <div v-else>
      <label>Email</label>
      <input placeholder="Enter your email address" key="email-input">
    </div>
    <button v-on:click="toggleType()">toggle login type</button>
    <!-- v-show 不管初始条件是什么，都会先渲染，v-if 是惰性的，如果初始条件为假，则直到它为真才开始渲染-->
    <div v-show="ok">hello this is v-show</div>
    <div v-show="no">hello this is v-show</div>
  </div>
</template>

<script>
export default{
  data () {
    return {
      ok: true,
      no: false,
      type: 'B',
      type1: 'G',
      loginType: 'username'
    }
  },
  methods: {
    toggleType: function () {
      if (this.loginType === 'username') {
        this.loginType = 'email'
      } else {
        this.loginType = 'username'
      }
    }
  }
}
</script>
