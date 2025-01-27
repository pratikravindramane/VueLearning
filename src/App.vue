<script>
export default {
  data() {
    return {
      name: 'Pratik Mane',
      status: true,
      tasks: ['Task One', 'Task Two', 'Task Three'],
    }
  },
  methods: {
    toggle() {
      this.status = !this.status
      console.log(this.status)
    },
  },
}
</script>
<template>
  <h1>{{ name }}</h1>
  <p v-if="status">User is Active</p>
  <p v-else>User is Inactive</p>
  <h3>Tasks:</h3>
  <ul>
    <li v-for="task in tasks" :key="task">
      {{ task }}
    </li>
  </ul>

  <button v-on:click="toggle">Toggle Status</button>
</template>

<style scoped></style>
