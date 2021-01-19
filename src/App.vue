<template>
  <div id="app">
    <AddTodo @add-todo="addTodo" />
    <Todos
      v-if="todos.length > 0"
      v-bind:todos="todos"
      @delete-todo="deleteTodo"
    />
    <h3 v-if="todos.length === 0" class="text">No more todos :)</h3>
  </div>
</template>

<script>
import Todos from "./components/Todos.vue";
import AddTodo from "./components/AddTodo.vue";
import axios from "axios";
export default {
  name: "App",
  components: {
    Todos,
    AddTodo,
  },
  data() {
    return {
      todos: [],
    };
  },
  methods: {
    deleteTodo(id) {
      axios
        .delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
        .then(() => (this.todos = this.todos.filter((todo) => todo.id !== id)))
        .catch((err) => console.log(err));
    },
    addTodo(newTodo) {
      const { title, completed } = newTodo;
      axios
        .post("https://jsonplaceholder.typicode.com/todos", {
          title,
          completed,
        })
        .then((res) => (this.todos = [...this.todos, res.data]))
        .catch((err) => console.log(err));
    },
  },
  created() {
    axios
      .get("https://jsonplaceholder.typicode.com/todos")
      .then((res) => (this.todos = [...res.data.slice(0, 5)]))
      .catch((err) => console.log(err));
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

#app {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 60px;
}

.text {
  margin-top: 20px;
}
</style>
