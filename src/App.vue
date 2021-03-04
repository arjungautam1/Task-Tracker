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
    async addTask(task) {
      const res = await fetch('api/tasks', {
        method: 'POST',
        headers: {
          'Content-type': 'application/json',

        },
        body: JSON.stringify(task)
      })
      const data = await res.json()
      this.tasks = [...this.tasks, data]
    },
    async deleteTask(id) {
      if (confirm('Do you sure want to delete the task ?')) {
        const res = await fetch(`api/tasks/${id}`, {
          method: 'DELETE'
        })
        res.status === 200 ? (this.tasks = this.tasks.filter((task) => task.id !== id)) : alert('Error deleting task ')
      }

    },
    async toggleReminder(id) {

      const taskToToggle = await this.fetchTask(id)
      const updTask = {
        ...taskToToggle, reminder: !taskToToggle.reminder
      }
      const res = await fetch(`api/tasks/${id}`, {
        method: 'PUT',
        headers: {
          'Content-type': 'application/json'
        },
        body: JSON.stringify(updTask)
      })
      const data=await res.json()

      this.tasks = this.tasks.map((task) =>
          task.id === id ?
              {...task, reminder:data.reminder} : task)
    },

    async fetchTasks() {
      const res = await fetch('api/tasks')
      const data = await res.json()

      return data
    },
    async fetchTask(id) {
      const res = await fetch(`api/tasks/${id}`)

      const data = await res.json()

      return data
    }
  },
  async created() {
    this.tasks = await this.fetchTasks()
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
