<template>
  <div class="todo-list">
    <todo-item v-for="todo in todos" :key="todo.id" :todoItem="todo" @change-state="todo.completed = $event.target.checked"></todo-item>
  </div>
</template>

<script>
import TodoItem from './TodoItem.vue'
export default {
  components: { TodoItem },
  name: "TodoList",
  props: ["todos"],
}
</script>

<style>
.todo-list {
  display: grid;
  row-gap: 14px;
}
</style>
