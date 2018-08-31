<script src="https://cdnjs.cloudflare.com/ajax/libs/velocity/1.2.3/velocity.min.js"></script>
<template>
  <div>
    <button @click="show1 = !show1">toggle</button>
    <transition name="fade"><p v-if="show1">hello</p></transition>
  </div>
</template>

<script>
export default{
  data () {
    return {
      show1: false,
      show2: false
    }
  }
}
</script>
<style>
  .fade-enter-active, .fade-leave-active {
    transition: opacity .5s;
  }

  .fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */
  {
    opacity: 0;
  }
</style>
