<script setup>
import ToDoForm from "./ToDoForm.vue";
import ToDoList from "./ToDoList.vue";
</script>
<template>
  <div class="todo-app">
    <h1>To Do List</h1>
    <to-do-form />
    <to-do-list />
  </div>
</template>
<style lang="scss" scoped>
.todo-app {
  width: 100%;

  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>