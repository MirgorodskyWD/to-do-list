<template>
  <li>
    <span class="left" v-bind:class="{done: todo.completed}">
      <input 
        v-model="todo.completed"
        @change="$emit('change-todo', todo.id)" 
        type="checkbox" 
      />
      <strong>{{ todoKey + 1 }}</strong>
      &nbsp;<input type="text" contenteditable v-model="todo.title" />
    </span>
    <button 
      @click="$emit('remove-todo', todo.id)" 
      class="rm"
    >&times;</button>
  </li>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true
    },
    todoKey: Number
  }
}
</script>

<style scoped>
  li {
    border: 1px solid #ccc;
    display: flex;
    justify-content: space-between;
    padding: .8em .8em;
    margin-bottom: .5em;
  }

  .left {
    display: flex;
  }

  .done {
    text-decoration: line-through;
  }

  .rm {
    background: #f56a6a;
    cursor: pointer;
    border: none;
    color: #fff;
    border-radius: 50%;
    font-weight: bold;
    transition: background-color .3s ease;
  }

  .rm:hover {
    background-color: #ff8686;
  }

  input[type="checkbox"] {
    margin-right: 1rem;
  }

  input[type="text"] {
    border: none;
    display: block;
    width: calc(90vw - 100px);
  }

  input[type="text"]:focus {
    outline: none;
  }
</style>