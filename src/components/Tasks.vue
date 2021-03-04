<template>
<div v-bind:key="task.id" v-for="task in tasks">
  <Task @toggle-reminder="$emit('toggle-reminder',task.id)"
      @delete-task="$emit('delete-task', task.id)"
        v-bind:task="task"/>
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
  emits:['delete-task','toggle-reminder'],
}
</script>

<style scoped>

</style>