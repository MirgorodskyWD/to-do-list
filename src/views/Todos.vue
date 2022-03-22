<template>
  <h2>Append some new tasks</h2>
  <router-link to="/">Back to Home Page</router-link>
  <hr class="back-home-hr">
  <add-to-do @add-todo="addTodo" />
  <hr>
  <loader v-if="loading" />
  <to-do-list
    v-else-if="todos.length"
    v-bind:todos="todos"
    @remove-todo="removeTodo"
    @change-todo="changeTodo"
  />
  <p v-else>There are no tasks at the moment.</p>
</template>

<script>
import AddToDo from '@/components/AddToDo';
import ToDoList from '@/components/ToDoList';
import Loader from '@/components/Loader';
export default {
  name: 'App',
  mounted() {
    fetch('https://jsonplaceholder.typicode.com/todos?_limit=5')
    .then(response => response.json())
    .then(json => {
      setTimeout(() => {
        this.todos = json;
        this.loading= false;
      }, 1000);
    });
  },
  data() {
    return {
      todos: [],
      loading: true
    };
  },
  components: {
    ToDoList, AddToDo, Loader
  },
  methods: {
    removeTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id);
    },
    addTodo(todo) {
      this.todos.push(todo);
    },
    changeTodo(id) {
      this.todos = this.todos.map(todo => {
        if (id === todo.id) todo.complete = !todo.complete;
        
        return todo;
      });
    }
  }
}
</script>

<style scoped>
.back-home-hr {
  margin: 2em 0 2em 0;
}
</style>