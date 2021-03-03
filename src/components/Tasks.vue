<template>
<div v-bind:key="task.id" v-for="task in tasks">
  <Task @delete-task="$emit('delete-task', task.id)" v-bind:task="task"/>
</div>
</template>

<script>
import Task from "@/components/Task";
export default {
  name: "Tasks",
  props:{
    tasks:Array
  },
  components:{
    Task
  },
  emits:['delete-task'],

}
</script>

<style scoped>

</style>