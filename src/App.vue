<template>
  <div class="container">
   <Header title="Task Tracker"/>
  </div>

</template>

<script>
import Header from "@/components/Header";
export default {
  name: 'App',
  components: {
    Header
  }
}
</script>

<style>
.container{
  max-width:500px;
  margin:30px auto;
  overflow :auto;
  min-height:300px;
  border :1px solid steelblue;
  padding :30px;
  border-radius:5px;

}
</style>
