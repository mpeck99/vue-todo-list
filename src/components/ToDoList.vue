<script setup>
import { useToDoListStore } from "../stores/todoList";
import { storeToRefs } from "pinia";

const store = useToDoListStore();
const { todoList } = storeToRefs(store);
const { toggleCompleted, deleteToDo } = store;
</script>
<template>
  <ul class="todolist" v-if="todoList.length > 0">
    <li
      v-for="todo in todoList"
      :key="todo.id"
      :class="{ completed: todo.completed }"
    >
      <span class="status" @click.stop="toggleCompleted(todo.id)"
        ><span class="check">&#10004;</span>
      </span>
      <span class="item">{{ todo.item }}</span>
      <span class="delete" @click="deleteToDo(todo.id)">&#128465;</span>
    </li>
  </ul>
  <div class="todolist" v-if="todoList.length == 0">
    <p>Looks like you have nothing to do. Start adding tasks</p>
  </div>
</template>
<style lang="scss" scoped>
.todolist {
  list-style-type: none;
  padding: 1rem;
  margin-top: 2rem;

  border-radius: 0.25rem;
  background: #fff;

  font-size: 2rem;

  color: #ff2281;
}

li {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 1rem;
  gap: 1rem;

  text-transform: capitalize;
  color: #ff2281;

  &.completed {
    opacity: 0.8;

    .check {
      display: block;
    }

    .item {
      text-decoration: line-through;
    }
  }
}

.status {
  width: 2.5rem;
  height: 2.5rem;

  cursor: pointer;
  border: 1px solid #a5a5a5;

  .check {
    display: none;

    text-align: center;
  }
}

.delete {
  padding: 0 0.75rem;
  margin-left: 2rem;

  background: #ff2281;
  color: #fff;
  border-radius: 0.25rem;
  font-size: 2rem;
  cursor: pointer;

  &:hover,
  &:focus {
    background: #f5006a;
  }
}
</style>