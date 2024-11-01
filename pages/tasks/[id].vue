<script setup>
const route = useRoute();
const id = route.params.id;
const {
  data: task,
  error,
  refresh,
  status,
} = await useLazyFetch(`https://jsonplaceholder.typicode.com/todos/${id}`);
</script>
<template>
  <button @click="refresh()">更新</button>
  <p v-if="error">{{ error }}</p>
  <p v-if="status === 'pending'">Loading ...</p>
  <div v-else>
    <p>Task ID: {{ task.id }}</p>
    <p>{{ task.title }}</p>
    <p>{{ task.completed }}</p>
  </div>
</template>
