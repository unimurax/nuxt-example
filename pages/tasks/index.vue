<script setup>
const {
  data: todos,
  error,
  refresh,
  status,
} = await useLazyFetch("https://jsonplaceholder.typicode.com/todos/");
</script>
<template>
  <h1>Tasks</h1>
  <button @click="refresh()">更新</button>
  <p v-if="error">{{ error }}</p>
  <p v-if="status === 'pending'">Loading ...</p>
  <ul v-else>
    <li v-for="todo in todos" :key="todo.id">
      <NuxtLink :to="`/tasks/${todo.id}`">{{ todo.title }}</NuxtLink>
    </li>
  </ul>
</template>
