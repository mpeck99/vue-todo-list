<script setup>
import ToDoApp from "./components/ToDoApp.vue";
</script>

<template>
  <main>
    <to-do-app />
  </main>
</template>

<style>
main {
  display: flex;
  flex-direction: column;
  align-items: center;

  padding: 1rem;
}

h1 {
  font-size: 3rem;
}
</style>
