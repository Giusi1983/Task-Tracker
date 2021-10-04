<template>
  <button v-on:click="onClick()" :style="{ background }" class="btn">{{ text }}</button>
</template>

<script>

export default {
  name: 'Button', 
  props: {
   text: String,
   color:String
  }, 
  methods: {
    onClick() {
      this.$emit('btn-click')
    },
  }
}
</script>

<style scoped>
.btn {
  width: 154px; 
  height:48px; 
  margin-right:10px;
}
</style>