<template>
  <div id="app">
    <h1>Список дел</h1>
    <TodoList />
  </div>
</template>

<script>
import TodoList from './components/TodoList.vue';

export default {
  components: {
    TodoList
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  margin-top: 60px;
}

h1 {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  font-size: 32px;
}
</style>
