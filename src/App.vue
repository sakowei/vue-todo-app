<template>
  <main>
    <div class="app">
      <h1>TODO List</h1>
       <TodoAdd :tid="todos.length" @add-todo="addTodo"/>
      <TodoFilter :selected="filter" @change-filter="filter = $event"/>
      <TodoList :todos="filteredTodos"/>
    </div>
  </main>
</template>

<script>
import {computed, ref} from 'vue';
import TodoAdd from './components/TodoAdd.vue';
import TodoList from './components/TodoList.vue';
import TodoFilter from './components/TodoFilter.vue';

export default {
  name: "App",
  components: { TodoAdd, TodoList, TodoFilter },
  setup() {
    const todos = ref([]);
    const addTodo = (todo) => todos.value.push(todo);
    const filter = ref('all');
    const filteredTodos = computed(() => {
      switch (filter.value) {
        case "done":
          return todos.value.filter((todo) => todo.completed);
        case "todo":
          return todos.value.filter((todo) => !todo.completed);
        default:
          return todos.value;
      }
    });
    return {
      todos,
      filter,
      filteredTodos,
      addTodo
    };
  }
}
</script>

<style>
@import url(../css/todo.css);
</style>
