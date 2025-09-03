<script setup>
import { ref } from 'vue';

let name=ref('Vue Master')
let status=ref(true)
const tasks=ref(['task 1', 'task 2', 'task 3'])
const newTask = ref('')

function changeStatus()
{
  status.value = status.value !== true;
}
function addTask() {
  if(newTask.value.trim() !== ''){
    tasks.value.push(newTask.value)
  }
  newTask.value = ''
}
function deleteTask(index) {
  tasks.value.splice(index,1)
}

</script>

<template>
  <h1>Vue Jobs for {{name}}</h1>
  <p v-if="status">User active</p>
  <p v-else>User inactive</p>
  <h3>
    <ul>
      <li v-for="(task,index) in tasks" :key="task">
        {{task}}
        <button @click="deleteTask(index)">X</button>
      </li>
    </ul>
  </h3>
  <button v-on:click="changeStatus">Change status</button>
  <form @submit.prevent="addTask">
    <label for="newTask">Add Task</label>
    <input type="text" id="newTask" name="newTask" v-model="newTask">
    <button type="submit">Add</button>
  </form>
</template>

<style scoped>

</style>
