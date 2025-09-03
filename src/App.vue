<script setup>
import { ref } from 'vue';

let name=ref('Vue Master')
let status=ref(true)
const tasks=ref(['task 1', 'task 2', 'task 3'])


function changeStatus()
{
  status.value = status.value !== true;
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
