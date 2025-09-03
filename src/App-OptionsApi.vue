
<script>
export default {
  data(){
    return{
      name:'Vue Master',
      status:true,
      tasks:['task 1', 'task 2', 'task 3']
    };
  },
  methods:{
    changeStatus(){
      if(this.status === true)
      {
        this.status = false
      }else
      {
        this.status = true
      }
    }
  }
}
</script>
<template>
  <h1>Vue Jobs for {{name}}</h1>
  <p v-if="status">User active</p>
  <p v-else>User inactive</p>
  <h3>
    <ul>
      <li v-for="task in tasks" :key="task">{{task}}</li>
    </ul>
  </h3>
  <button v-on:click="changeStatus">Change status</button>
</template>

<style scoped>

</style>
