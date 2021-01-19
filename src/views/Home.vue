<template>
  <div class="homeWrapper">
    <div class="container">
      <AddTodo @add-todo="addTodo" />
      <Todos
        v-if="todos.length > 0"
        v-bind:todos="todos"
        @delete-todo="deleteTodo"
      />
      <h3 v-if="todos.length === 0" class="text">No more todos :)</h3>
    </div>
  </div>
</template>

<script>
import Todos from "../components/Todos.vue";
import AddTodo from "../components/AddTodo.vue";
import axios from "axios";
export default {
  name: "Home",
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

<style scoped>
.homeWrapper {
  padding: 10px;
}

.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin: auto;
  margin-top: 30px;
  max-width: 700px;
  width: 100%;
  border-radius: 5px;
  padding: 15px;
  background-color: rgb(185, 185, 185);
}

.text {
  margin-top: 20px;
}
</style>
