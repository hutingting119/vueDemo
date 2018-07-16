<template>
    <div>
      <!-- 数组v-for1-->
      <ul>
        <li v-for="item in items">{{item.message}}</li>
      </ul>
      <!-- 数组v-for2-->
      <ul>
        <li v-for="(item,index) in items">{{index}}-{{item.message}}</li>
      </ul>
      <!-- 数组v-for-of-->
      <ul>
        <li v-for="item of items">{{item.message}}</li>
      </ul>
      <!--对象v-for1-->
      <ul>
        <li v-for="value in object">{{value}}</li>
      </ul>
      <!--对象v-for2-->
      <ul>
        <li v-for="(value,key) in object">{{key}}: {{value}}</li>
      </ul>
      <!--对象v-for3-->
      <ul>
        <li v-for="(value,key,index) in object">{{index}}.{{key}}: {{value}}</li>
      </ul>
      <span>数组更新检测</span>
      <button v-on:click="items.push({message:'Baz'})">push</button>
      <button v-on:click="items.pop()">pop</button>
      <button v-on:click="items.shift()">shift</button>
      <button v-on:click="items.unshift({message:'unshift'})">unshift</button>
      <button v-on:click="items.splice(2,0,{message:'splice'})">splice</button>
      <button v-on:click="(items.sort())">sort</button>
      <button v-on:click="(items.reverse())">reverse</button>
      <div>
        <span>有时，我们想要显示一个数组的过滤或排序副本，而不实际改变或重置原始数据。在这种情况下，可以创建返回或排序数组的计算属性</span>
        <ul>
          <li v-for="n in evenNumbers">{{n}}</li>
        </ul>
        <span>在计算属性不适用的情况下，我们用method方法</span>
        <ul>
          <li v-for="n in even(methodNumbers)">{{ n }}</li>
        </ul>
      </div>
      <div>
        <span>v-for on a div，类似于v-if,利用带有v-for的div渲染多个元素</span>
        <ul>
          <div v-for="number in numbers">
            <li>{{ number}}</li>
            <li class="divider" role="presentation"></li>
          </div>
        </ul>
      </div>
    </div>
</template>

<script>
export default{
  data () {
    return {
      items: [
        {message: 'Foo'},
        {message: 'Bar'}
      ],
      object: {
        firstName: 'John',
        lastName: 'Doe',
        age: 30
      },
      numbers: [1, 2, 3, 4, 5],
      methodNumbers: [9,8,7,6,5,4,3]
    }
  },
  computed: {
    evenNumbers: function () {
      return this.numbers.filter(function (number) {
        return number % 2 === 0
      })
    }
  },
  methods: {
    even: function (methodNumbers) {
      return methodNumbers.filter(function (methodNumber) {
        return methodNumber%2 === 0
      })
    }
  }
}
</script>
