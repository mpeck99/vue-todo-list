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
  <div>
    <form @submit.prevent="addItemAndClear(todo)">
      <label for="todo">Create new ToDo item</label>
      <div class="form-group-row">
        <input type="text" v-model="todo" id="todo" />
        <button>Add item</button>
      </div>
    </form>
  </div>
</template>
<style lang="scss" scoped>
label {
  font-weight: 700;
  font-size: 1.5rem;
}
</style>