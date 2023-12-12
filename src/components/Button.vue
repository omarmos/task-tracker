/* eslint-disable */
<template>
<button @click="onClick()" :style="{background:color}" class="btn" > {{ text }}</button>
  
</template>

<script>
export default{
  // eslint-disable-next-line
  name: 'Button',
  props:{
    text:String,
    color:String
  },
  
  methods: {
    onClick(){
    console.log("clicked")
  }
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>