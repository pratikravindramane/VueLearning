<script setup>
import { ref, onMounted } from 'vue'
const name = ref('Pratik Mane')
const status = ref(true)
const newTask = ref('')
let tasks = ref(['Task One', 'Task Two', 'Task Three'])
const toggle = () => {
  status.value = !status.value
}

const addTask = () => {
  if (newTask.value.trim() == '') return
  tasks.value.push(newTask.value)
  newTask.value = ''
}
const deleteTask = (val) => {
  tasks.value.splice(val, 1)
}
onMounted(async () => {
  try {
    const res = await fetch('https://jsonplaceholder.typicode.com/todos')
    const data = await res.json()
    tasks.value = data?.map((e) => e.title)
  } catch (error) {
    console.log(error)
  }
})
</script>
<template>
  <h1>{{ name }}</h1>
  <p v-if="status">User is Active</p>
  <p v-else>User is Inactive</p>
  <input type="text" name="tasks" id="tasks" v-model="newTask" />
  <button @click="addTask">submit</button>
  <h3>Tasks:</h3>
  <ul>
    <li v-for="(task, index) in tasks" :key="task">
      {{ task }}
      <button @click="deleteTask(index)">x</button>
    </li>
  </ul>

  <button v-on:click="toggle">Toggle Status</button>
</template>

<style scoped></style>
