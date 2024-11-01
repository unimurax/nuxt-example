<script setup>
const {
  data: todos,
  error,
  refresh,
  status,
} = await useLazyFetch("https://jsonplaceholder.typicode.com/todos/");
</script>
<template>
  <h1 class="title">Tasks</h1>
  <button class="btn btn-blue mt-4" @click="refresh()">更新</button>
  <p v-if="error">{{ error }}</p>
  <p v-if="status === 'pending'">Loading ...</p>
  <ul v-else>
    <li v-for="todo in todos" :key="todo.id">
      <NuxtLink class="card mt-4" :to="`/tasks/${todo.id}`">{{ todo.title }}</NuxtLink>
    </li>
  </ul>
</template>
