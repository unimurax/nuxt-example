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
  <button class="btn btn-blue mt-4" @click="refresh()">更新</button>
  <p v-if="error">{{ error }}</p>
  <p v-if="status === 'pending'">Loading ...</p>
  <div v-else class="card mt-4">
    <p>Task ID: {{ task.id }}</p>
    <p>{{ task.title }}</p>
    <p>{{ task.completed }}</p>
  </div>
</template>
