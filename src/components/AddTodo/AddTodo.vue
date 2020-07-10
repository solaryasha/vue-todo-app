<template>
  <form @submit.prevent="addTodo">
    <input 
      type="text"
      v-model="title"
      placeholder="What do you want to do ?"
    >
    <button type="submit">Add +</button>
  </form>
</template>
<script>
import { v4 as uuidv4 } from 'uuid';

export default {
  name: "AddTodo",
  data() {
    return {
      title: '',
    }
  },

  methods: {
    addTodo() {
      const newTodo = {
        id: uuidv4(),
        title: this.title,
        completed: false,
      }
      this.$emit('add-todo', newTodo);
      this.title= '';
    }
  }
}
</script>
<style scoped>
  
</style>