<template>
  <div>
    <ul>
      <to-do-item 
        v-bind:todo="todo" 
        v-bind:key="todo.id" 
        v-bind:todoKey="todoKey" 
        v-for="(todo, todoKey) in todos" 
        @remove-todo="removeTodo"
        @change-todo="changeTodo"
      />
    </ul>
  </div>
</template>

<script>
import ToDoItem from '@/components/ToDoItem';

export default {
  props: ['todos'],
  components: {
    ToDoItem
  },
  methods: {
    removeTodo(id) {
      this.$emit('remove-todo', id);
    },
    changeTodo(id) {
      this.$emit('change-todo', id);
    }
  }
};
</script>

<style scoped>
  ul {
    list-style: none;
    margin: 0;
    padding: 0;
  }
</style>