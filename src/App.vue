<template>
  <div class="container">
    <Header title="Task Tracker"/>
    <Tasks v-bind:tasks="tasks"/>
  </div>

</template>

<script>
import Header from "@/components/Header";
import Tasks from "@/components/Tasks";

export default {
  name: 'App',
  components: {
    Header,
    Tasks
  },
  data() {
    return {
      tasks: []
    }
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
          id: 2,
          text: 'PhotoGraphy at Kathmandu Mall',
          day: 'March 20th at 10AM',
          remainder: false
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
