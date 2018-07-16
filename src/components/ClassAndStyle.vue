<template>
  <div>
    <!--对象语法1-->
    <div v-bind:class="{active:isActive}">对象语法1</div>
    <div v-bind:class="{active:notActive}">对象语法1</div>
    <!--对象语法2-->
    <div class="static" v-bind:class="{active2:isActive2,'text-danger':hasError}">对象语法2</div>
    <div class="static" v-bind:class="{active2:isActive3,'text-danger':hasError1}">对象语法2</div>
    <!--对象语法3-->
    <div class="static" v-bind:class="classObject">对象语法3</div>
    <div class="static" v-bind:class="classObject1">对象语法3</div>
    <!--对象语法4-->
    <div v-bind:class="classObject2">对象语法4</div>
    <div v-bind:class="classObject3">对象语法4</div>
    <!--数组语法1-->
    <div v-bind:class="[arrNumOne,arrNumTwo]">数组语法1</div>
    <!--数组语法2-->
    <div v-bind:class="[true ? arrNumOne : '',arrNumTwo]">数组语法2</div>
    <div v-bind:class="[false ? arrNumOne : arrNumThree,arrNumTwo]">数组语法2</div>
    <!--对象语法1-->
    <div v-bind:style="{color:isColor,fontsize:fontSize+'px'}">对象语法1</div>
    <!--对象语法2-->
    <div v-bind:style="styleObject">对象语法2</div>
  </div>
</template>

<script>
export default{
  data () {
    return {
      // 对象语法1
      isActive: true,
      notActive: false,
      // 对象语法2
      isActive2: true,
      isActive3: false,
      hasError: false,
      hasError1: true,
      // 对象语法3
      classObject: {
        active: true,
        'text-danger': false
      },
      classObject1: {
        active: false,
        'text-danger': true
      },
      // 数组语法
      arrNumOne: 'arrOneStyle',
      arrNumTwo: 'arrTwoStyle',
      arrNumThree: 'arrThreeStyle',
      // 对象语法1
      isColor: 'red',
      fontSize: 20,
      styleObject: {
        color: 'yellow',
        fontSize: '21px'
      }
    }
  },
  // 对象语法4
  computed: {
    classObject2: function () {
      return {
        active: this.isActive && !this.error,
        'text-danger': this.error && this.error.type === 'fatal'
      }
    },
    classObject3: function () {
      return {
        active: !this.isActive && !this.error,
        'text-danger': !this.error && false
      }
    }
  }
}
</script>
<style>
  .active{
    color: #3a33d1;
  }
  .active2{
    color:darkslategray;
  }
  .text-danger{
    font-size: 50px;
  }
  .static{
    width: 100px;
    background-color: #8cc5ff;
  }
  .arrOneStyle{
    color: #5daf34;
    width: 80px;
  }
  .arrTwoStyle{
    background-color: red;
    height: 40px;
  }
  .arrThreeStyle{
    width: 85px;
  }
</style>
