<template>
  <div class="todosWrapper">
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
.todosWrapper {
  display: flex;
  flex-direction: column;
  background-color: rgb(236, 236, 236);
  width: 100%;
}

.todo {
  padding: 15px 10px;
}

.todo:not(:last-child) {
  border-bottom: 1px solid rgb(185, 185, 185);
}
</style>
