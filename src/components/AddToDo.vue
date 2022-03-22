<template>
  <form @submit.prevent="onSubmit">
    <input v-model="title" type="text" placeholder="Type in some text...">
    <button>Create a task</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      title: ''
    };
  },
  methods: {
    onSubmit() {
      if (this.title.trim) {
        const newToDo = {
          id: Date.now(),
          title: this.title,
          completed: false
        };

        this.$emit('add-todo', newToDo);

        this.title = '';
      }
    }
  }
}
</script>


<style scoped>
form {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

input {
  border: 1px solid rgb(170, 170, 170);
  border-radius: 3px;
  box-sizing: border-box;
  height: 50px;
  padding: 0 .8em;
  transition: border-color .5s ease;
  width: calc(100% - 300px - 10px);
}

input:hover {
  border-color: #0065ff;
}

input:focus {
  outline: none;
}

button {
  box-sizing: border-box;
  background: #0065ff;
  background-image: linear-gradient(90deg, #0065ff, #6942ef, #6554c0, #008cff, #0065ff, #6942ef);
  background-size: 400%;
  background-position: 0% 0%;
  border-radius: 3px;
  color: #fff;
  cursor: pointer;
  border: none;
  -webkit-appearance: none;
  height: 50px;
  margin: 0;
  padding: 0;
  width: 300px;
}

button:hover {
  animation: gradientRotate 1s infinite;
}

@keyframes gradientRotate {
  0% {
    background-position: 0% 0%;
  }
  100% {
    background-position: 100% 100%;
  }
}
</style>