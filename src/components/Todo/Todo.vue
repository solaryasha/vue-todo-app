<template>
  <div 
    class="todo-item" 
    :class="{'is-complete': todo.completed}"
  > 
    <div class="todo-item__content">
      <input 
      type="checkbox"
      class="todo-item__checkbox"
      @change="markComplete"
      >
      <div class="todo-item__title">
        <p v-if="!shouldEdit">{{ todo.title }}</p>
        <input 
          type="text"
          v-model="todo.title"
          v-if="shouldEdit"
          class="todo-item__edit"
        >
      </div>
    </div>
    <div class="buttons">
      <button class="button">
        <img 
          src="../../assets/pencil.svg"
          class="edit"
          @click="editTodo"
        />
      </button>
      <button @click="$emit('del-todo',todo.id)" class="del">x</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Todo",
  props: ["todo"],
  data() {
    return {
      shouldEdit: false,

    }
  },
  methods: {
    markComplete() {
      this.todo.completed = !this.todo.completed;
      this.shouldEdit = !this.shouldEdit;
    },
    editTodo() {
      this.shouldEdit = !this.shouldEdit;
    }

  }
}
</script>

<style scoped>
  .todo-item {
    display: flex;
    justify-content: space-between;
    align-items: center;
    background: #f4f4f4;
    padding: 10px;
    border-bottom: 1px #ccc dotted;
  }
  .todo-item__content {
    display: flex;
    align-items: center;
  }
  .todo-item__checkbox {
    margin-right: 1rem;
  }

  .todo-item__edit {
    border: none;
    outline: none;
    background-color: #f4f4f4;
  }
  .buttons {
    display: flex;
    align-items: center;
  }

  .button {
    outline: none;
    border: none;
    margin-right: 2rem;
  }

  .edit {
    display: inline-block;
    width: 20px;
    height: 20px;
    cursor: pointer;
  }
  .is-complete {
    text-decoration: line-through;
  }
  .del {
    background: #ff0000;
    color: #fff;
    border: none;
    padding: 5px 9px;
    border-radius: 50%;
    cursor: pointer;
  }
</style>