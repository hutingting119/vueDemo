<template>
    <div>
      <div>
        <div>v-on指令监听DOM事件</div>
        <button v-on:click="counter+=1">Add</button>
        <p>The button above has been clicked {{ counter }}times.</p>
      </div>
      <div>
        <div>把事件处理放在JS中</div>
        <button v-on:click="greet">Greet</button>
      </div>
      <div>
        <div>内联处理器中的方法，在内联JS语句中调用方法</div>
        <button v-on:click="say('hi')">say hi</button>
      </div>
      <div>
        <div>有时也需要在内联语句处理器中访问原始的DOM事件，可以用特殊变量$event把它传入方法</div>
        <button v-on:click="warn('Form cannot be submitted yet',$event)">Submit</button>
      </div>
      <div>
        <div>当点击父元素的时候，执行doThis,当点击子元素a的时候，这个点击动作不单单触发了a标签，同时也触发了div标签，这就是事件冒泡，
          所以假设上述例子中a标签为v-on:click='doThis',则doThis会被执行两次，父元素和子元素都执行了一次click事件，而.stop则是阻止事
          件冒泡，再次点击a标签，click事件只会执行一次</div>
        <div @click='doThis()'>
          点击父元素
          <a v-on:click.stop="doThis()">点击子元素
          </a>
        </div>
        <div @click='doThis()'>
          点击父元素
          <a v-on:click="doThis()">点击子元素,没有stop事件
          </a>
        </div>
      </div>
      <div>
        <button v-on:click="say('hi')">点击</button>
        <button v-on:keyup.enter="say('hi')">点击回车键</button>
      </div>
    </div>
</template>

<script>
export default{
  data () {
    return {
      counter: 0,
      name: 'Vue.js'
    }
  },
  methods: {
    greet: function (event) {
      alert('Hello' + this.name + '!')
      if (event) {
        alert(event.target.tagName)
      }
    },
    say: function (message) {
      alert(message)
    },
    warn: function (message, event) {
      if (event)event.preventDefault()
      alert(message)
    },
    doThis: function () {
      alert('hahaha')
    }
  }
}
</script>
