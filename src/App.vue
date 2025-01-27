<script setup>
import { ref } from 'vue'
const name = ref('Pratik Mane')
const status = ref(true)
const newTask = ref('')
let tasks = ref(['Task One', 'Task Two', 'Task Three'])
const toggle = () => {
  this.status = !this.status
  console.log(this.status)
}

const addTask = () => {
  if (newTask.value.trim() == '') return
  tasks.value.push(newTask.value)
  newTask.value = ''
}
</script>
<template>
  <h1>{{ name }}</h1>
  <p v-if="status">User is Active</p>
  <p v-else>User is Inactive</p>
  <input type="text" name="tasks" id="tasks" v-model="newTask" />
  <button @click="addTask">submit</button>
  <h3>Tasks:</h3>
  <ul>
    <li v-for="task in tasks" :key="task">
      {{ task }}
    </li>
  </ul>

  <button v-on:click="toggle">Toggle Status</button>
</template>

<style scoped></style>
