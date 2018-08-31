<template>
  <div class="hello">
    <!--<grammer></grammer>-->
    <!--<listen></listen>-->
    <!--<classAndStyle></classAndStyle>-->
    <!--<conditionlRender></conditionlRender>-->
    <!--<listRender></listRender>-->
    <!--<evenProcess></evenProcess>-->
    <!--<formInput></formInput>-->
    <!--<componentBasis></componentBasis>-->
    <!--<propExercise></propExercise>-->
    <!--<customEvent></customEvent>-->
    <!--<slotDemo></slotDemo>-->
    <!--<dynAsyn></dynAsyn>-->
    <!--<bouSitua></bouSitua>-->
    <!--<refParent></refParent>-->
    <!--<refChild></refChild>-->
    <!--<comTransition></comTransition>-->
    <!--<cpdf></cpdf>-->
    <!--<route></route>-->
    <router-link to="/Cpdf">Go to Bar</router-link>
  </div>
</template>

<script>
import grammer from './Grammar.vue'
import listen from './Listen.vue'
import classAndStyle from './ClassAndStyle.vue'
import conditionlRender from './ConditionalRender.vue'
// import listRender from './ListRender.vue'
import evenProcess from './EventProcess.vue'
// import formInput from './FormInput.vue'
import componentBasis from './ComponentBasis.vue'
import propExercise from './PropExercise.vue'
import customEvent from './CustomEvent.vue'
// import slotDemo from './SlotDemo.vue'
import dynAsyn from './DynAsyn.vue'
// import bouSitua from './BouSitua.vue'
import refParent from './ref-parent.vue'
import refChild from './ref-child.vue'
import comTransition from './ComTransition.vue'
import cpdf from './Cpdf.vue'
export default {
  name: 'HelloWorld',
  components: {
    grammer,
    listen,
    classAndStyle,
    conditionlRender,
    // listRender,
    evenProcess,
    // formInput,
    componentBasis,
    propExercise,
    customEvent,
    // slotDemo
    dynAsyn,
    // bouSitua,
    refParent,
    refChild,
    comTransition,
    cpdf
  }
}
</script>
