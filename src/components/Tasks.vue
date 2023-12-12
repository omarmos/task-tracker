/* eslint-disable */
<template>
<div  :key="task.id" v-for="task in tasks" >
<Task :task="task"/>
</div>
</template>

<script>
import Task from './Task.vue'
export default {
  // eslint-disable-next-line
  name: 'Tasks',
  props: {
    tasks: Array
  },
  components:{
    Task
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>