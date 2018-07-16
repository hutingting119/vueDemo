<template>
  <div class="hello">
    <!--<grammer></grammer>-->
    <!--<listen></listen>-->
    <!--<classAndStyle></classAndStyle>-->
    <!--<conditionlRender></conditionlRender>-->
    <listRender></listRender>
  </div>
</template>

<script>
import grammer from './Grammar.vue'
import listen from './Listen.vue'
import classAndStyle from './ClassAndStyle.vue'
import conditionlRender from './ConditionalRender.vue'
import listRender from './ListRender.vue'
export default {
  name: 'HelloWorld',
  components: {
    grammer,
    listen,
    classAndStyle,
    conditionlRender,
    listRender
  }
}
</script>
