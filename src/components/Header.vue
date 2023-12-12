/* eslint-disable */
<template>
  <header>
    <h1>{{ title }}</h1>
  </header>
  <Button color="green" text="Add Task"  />
</template>

<script>

import Button from './Button.vue'
export default {
  // eslint-disable-next-line
  name: 'Header',
  props: {
    title: String
  },

  components:{
    Button
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
header {
  
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
  padding-right: 100px;
  display: inline-block;
}
</style>