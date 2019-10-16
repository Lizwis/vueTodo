<template>
  <div>
    <form @submit="addtodo">
      <input type="text" v-model="title" name="title" />
      <input type="submit" value="submit" class="btn" />
    </form>
  </div>
</template>

<script>
export default {
  name: "addtodo",

  data() {
    return {
      title: ""
    };
  },
  methods: {
    addtodo(e) {
      e.preventDefault();
      const newTodo = {
        title: this.title,
        completed: false
      };
      //Send to parent
      this.$emit("add-todo", newTodo);
      this.title = "";
    }
  }
};
</script>

<style scoped>
form {
  display: flex;
}

input[type="text"] {
  flex: 10;
  padding: 5px;
}

input[type="submit"] {
  flex: 2;
}
</style>