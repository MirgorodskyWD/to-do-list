<template>
  <h1>To-Do application</h1>
  <add-to-do @add-todo="addTodo" />
  <hr>
  <router-view />
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

a {
  color: #0065ff;
}

hr {
  padding: 0;
  height: 0;
  border: none;
  border-top: 1px solid #d3d3d3;
}
</style>
