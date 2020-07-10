<template>
  <div id="app">
    <Header />
    <AddTodo 
    @add-todo="addTodo"
    />
    <TodoList 
    :todos="todos"
    @del-todo="deleteTodo"
    />
  </div>
</template>

<script>
import TodoList from './components/TodoList/TodoList';
import Header from './components/Header/Header';
import AddTodo from './components/AddTodo/AddTodo';

export default {
  name: 'App',
  components: {
    TodoList,
    Header,
    AddTodo,
  },
  data() {
    return {
      todos: [],
    }
  },
  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id);
    },
    addTodo(todo) {
      this.todos = [...this.todos, todo]
    }
  }
}
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
</style>
