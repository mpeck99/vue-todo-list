<script setup>
import { ref } from "vue";
import { useToDoListStore } from "../stores/todoList";

const todo = ref("");
const store = useToDoListStore();

function addItemAndClear(item) {
  if (item.length === 0) {
    return;
  }
  store.addToDo(item);
  todo.value = "";
}
</script>
<template>
  <form @submit.prevent="addItemAndClear(todo)">
    <label for="todo">Create new ToDo item</label>
    <div class="form-group">
      <input type="text" v-model="todo" id="todo" />
      <button>Add item</button>
    </div>
  </form>
</template>
<style lang="scss" scoped>
label {
  font-weight: 700;
  font-size: 1.5rem;
}

.form-group {
  display: flex;
  align-items: flex-start;

  margin-top: 0.5rem;
}

input {
  padding: 0.83rem;
  border: 0;

  box-shadow: none;
  border-top-left-radius: 0.25rem;
  border-bottom-left-radius: 0.25rem;
}

button {
  padding: 0.75rem 1rem;

  border: none;
  border-top-right-radius: 0.25rem;
  border-bottom-right-radius: 0.25rem;
  box-shadow: none;
  background: #ff2281;

  color: #fff;
  font-weight: 700;
  font-size: 1rem;

  &:hover,
  &:focus {
    background: #f5006a;
    cursor: pointer;
  }
}
</style>