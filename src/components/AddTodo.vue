<template>
  <div class="addTodoWrapper">
    <input type="text" v-model="newTodo" placeholder="Add todo..." @keyup.enter="handleEnter"/>
    <button type="submit" @click="handleSubmit">Submit</button>
  </div>
</template>

<script>
export default {
  name: "AddTodo",
  data() {
    return {
      newTodo: "",
    };
  },
  methods: {
    handleSubmit() {
      const newTodo = {
        title: this.newTodo,
        completed: false,
      };

      this.$emit("add-todo", newTodo);
      this.newTodo = "";
    },

    handleEnter() {
        this.handleSubmit()
    }
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.addTodoWrapper {
  display: flex;
  width: 100%;
}

input {
  padding: 5px 10px;
  flex: 10;
  font-size: 1.2rem;
  border: none;
}

input:focus {
  outline: none;
}

button {
  padding: 4px 8px;
  border: none;
  cursor: pointer;
  flex: 2;
  background-color: rgb(80, 80, 80);
  color: white;
}

button:hover {
  background-color: black;
}
</style>
