<template>
  <div class="container">
    <Header @toggle-add-task="toggleAddTask" title="Task Tracker"/>
    <div v-if="showAddTask">
      <AddTask @add-task="addTask"/>
    </div>

    <Tasks @toggle-reminder="toggleReminder"
           @delete-task="deleteTask"
           :tasks="tasks"/>
  </div>

</template>

<script>
import Header from "@/components/Header";
import Tasks from "@/components/Tasks";
import AddTask from "@/components/AddTask";

export default {
  name: 'App',
  components: {
    Header,
    Tasks,
    AddTask
  },
  data() {
    return {
      tasks: [],
      showAddTask: false
    }
  },
  methods: {
    toggleAddTask() {
      this.showAddTask = !this.showAddTask
    },
    addTask(task) {
      this.tasks = [...this.tasks, task]
    },
    deleteTask(id) {
      if (confirm('Do you sure want to delete the task ?'))
        this.tasks = this.tasks.filter((task) => task.id !== id)
    },
    toggleReminder(id) {
      this.tasks = this.tasks.map((task) => task.id === id ? {...task, reminder: !task.reminder} : task)
    },

  },
  created() {
    this.tasks = [{
      id: 1,
      text: 'Shopping for Dad and Bro',
      day: 'March 3rd at 6:30pm',
      remainder: true
    },
      {
        id: 2,
        text: 'PhotoGraphy at Kathmandu Mall',
        day: 'March 20th at 10AM',
        remainder: false
      },
      {
        id: 3,
        text: 'PhotoGraphy at Kathmandu Mall',
        day: 'March 20th at 10AM',
        remainder: true
      }
    ]
  }
}
</script>

<style>
.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}

.btn {
  display: inline-block;
  background: black;
  color: white;
  padding: 10px 20px;
  margin: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
</style>
