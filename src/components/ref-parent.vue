<template>
  <div>
    <refChild ref="child"></refChild>
    <button @click="change">change</button>
  </div>
</template>

<script>
import refChild from './ref-child.vue'
export default {
  name: 'HelloWorld',
  components: {
    refChild
  },
  methods: {
    change: function () {
      this.$refs.child.str = 'world'
    }
  }
}
</script>
