<template>
  <div class="wrapper">
    <div
      v-for="todo in todos"
      v-bind:key="todo.id"
      class="todo"    
    >
      <TodoItem :todo="todo" @delete-todo="$emit('delete-todo', todo.id)" />
    </div>
  </div>
</template>

<script>
import TodoItem from "./TodoItem.vue";

export default {
  name: "Todos",
  components: {
    TodoItem,
  },
  props: ["todos"],
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.wrapper {
  display: flex;
  flex-direction: column;
  background-color: rgb(236, 236, 236);
  width: 500px;
  border: 1px solid black;
}

.todo {
  padding: 10px;
}

.todo:not(:last-child) {
  border-bottom: 1px solid black;
}
</style>
