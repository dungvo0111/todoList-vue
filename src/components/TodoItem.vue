<template>
  <div class="todoWrapper">
    <input
      type="checkbox"
      @change="markCompleted"
      class="checkbox"
      :value="todo.completed"
      :checked="todo.completed"
      
    />
    <p class="todo" :class="{ completed: todo.completed }">
      {{ todo.title }}
    </p>
    <button @click="handleDelete" class="deleteButton">x</button>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todo"],
  methods: {
    markCompleted() {
      this.todo.completed = !this.todo.completed;
    },

    handleDelete(todo) {
      this.$emit("delete-todo", todo.id);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.todoWrapper {
  display: flex;
  align-items: center;
  position: relative;
}

.checkbox {
  cursor: pointer;
}

.todo {
  margin-left: 10px;
}

.completed {
  text-decoration: line-through;
}

.deleteButton {
  background-color: red;
  color: white;
  border-radius: 50%;
  height: 20px;
  width: 20px;
  cursor: pointer;
  border: none;
  position: absolute;
  right: 5px;
}

.deleteButton:hover {
  opacity: 0.6;
}
</style>
