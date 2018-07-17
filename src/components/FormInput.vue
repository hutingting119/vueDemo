<template>
    <div>
      <div>
        <p>基础用法</p>
        <input v-model="message" placeholder="edit me">
        <p>message is :{{ message }}</p>
      </div>
      <div>
        <p>多行文本</p>
        <span>Multiline message is:</span>
        <p style="white-space: pre-line;">{{ message }}</p>
        <br>
        <textarea v-model="message" placeholder="edit me"></textarea>
      </div>
      <div>
        <div>复选框</div>
        <input type="checkbox" id="checkbox" v-model="checked">
        <label for="checkbox">{{checked}}</label>
        <div>
          <input type="checkbox" id="jack" value="jack" v-model="checkNames">
          <label for="jack">Jck</label>
          <input type="checkbox" id="john" value="john" v-model="checkNames">
          <label for="john">john</label>
          <input type="checkbox" id="miumiu" value="miumiu" v-model="checkNames">
          <label for="miumiu">miumiu</label>
          <div>check nams:{{ checkNames }}</div>
        </div>
      </div>
      <div>
        <div>单选按钮</div>
        <input type="radio" id="one" value="one" v-model="picked">
        <label for="one">one</label>
        <br>
        <input type="radio" id="two" value="two" v-model="picked">
        <label for="two">two</label><br>
        <div>picked:{{ picked }}</div>
      </div>
      <div>
        <div>选择框</div>
        <select v-model="selected">
          <option disabled value="">请选择</option>
          <option>A</option>
          <option>B</option>
          <option>C</option>
        </select>
        <span>selected:{{ selected }}</span>
      </div>
      <div>
        <div>v-for动态选项</div>
        <select v-model="selected">
          <option v-for="option in options" v-bind:value="option.value">{{option.text}}</option>
        </select>
        <span>selected:{{ selected }}</span>
      </div>
    </div>
</template>

<script>
export default{
  data () {
    return {
      message: 'this is formInput',
      checked: false,
      checkNames: [],
      picked: '',
      selected: '',
      options: [
        {text: 'one', value: 'A'},
        {text: 'two', value: 'B'},
        {text: 'three', value: 'C'}
      ]
    }
  }
}
</script>
