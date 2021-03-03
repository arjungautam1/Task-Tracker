<template>
  <div class="task">
    <h3>{{task.text}}</h3>
    <p>{{task.day}}</p>
  </div>
</template>

<script>
export default {
  name: "Task",
  props:{
    task:Object
  }
}
</script>

<style scoped>
.task{
  background: #f4f4f4;
  margin :5px;
  padding:10px 20px;
  cursor: pointer;
}
</style>