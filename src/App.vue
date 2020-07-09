<template>
  <div id="app">
    <TodoList 
    :todos="todos"
    @del-todo="deleteTodo"
    />
  </div>
</template>

<script>
import TodoList from './components/TodoList/TodoList'

export default {
  name: 'App',
  components: {
    TodoList
  },
  data() {
    return {
      todos: [
        {
          userId: 1,
          id: 1,
          title: 'Todo 1',
          completed: false,
        },
        {
          userId: 1,
          id: 2,
          title: 'Todo 2',
          completed: false,
        },
        {
          userId: 1,
          id: 3,
          title: 'Todo 3',
          completed: false,
        },
        {
          userId: 1,
          id: 4,
          title: 'Todo 4',
          completed: false,
        },
        {
          userId: 1,
          id: 5,
          title: 'Todo 5',
          completed: false,
        },
      ]
    }
  },
  methods: {
    deleteTodo(id){
      this.todos = this.todos.filter(todo => todo.id !== id);
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
