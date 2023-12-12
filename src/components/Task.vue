/* eslint-disable */
<template>
  <div :class="[task.reminder ? 'reminder' : '', 'task']">
    <h3>{{ task.text }}
    <i class="fas fa-times"></i>
    </h3>
    <p>{{ task.day }}</p>

  </div>

</template>

<script>
export default {
  // eslint-disable-next-line
  name: 'Task',
  props: {
    task: Object
  },


}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scope>
.fas {
  color: red;
}

.task {
  background: #f4f4f4;
  margin: 5px;
  padding: 10px 20px;
  cursor: pointer;
}

.task.reminder {
  border-left: 5px solid green;
}

.task h3 {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>