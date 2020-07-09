<template>
  <div>
    <div :key="todo.id" v-for="todo in todos">
       <Todo :todo="todo"/>
    </div>
  </div>
</template>

<script>
import Todo  from '../Todo/Todo';

export default {
  name: "TodoList",
  components: {
    Todo,
  },
  props: ['todos']
}
</script>

<style scoped>

</style>