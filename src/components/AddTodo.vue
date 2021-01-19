<template>
  <div class="wrapper">
    <input type="text" v-model="newTodo" placeholder="Add todo..." />
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
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.wrapper {
  display: flex;
  width: 500px;
}

input {
  width: 100%;
  padding: 5px 10px;
}

button {
  padding: 4px 8px;
}
</style>
