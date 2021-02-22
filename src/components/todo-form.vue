<template>
  <form @submit="handleSubmit">
    <label>
      <input type="text" ref="title" v-model="title" placeholder="Title..." />
      <input type="text" v-model="description" placeholder="Description..." />
    </label>
    <button>Add</button>
  </form>
</template>

<script>
export default {
  name: "todo-form",
  data: () => ({
    title: "",
    description: "",
  }),
  methods: {
    handleSubmit(event) {
      // Prevents form from submitting and reloading page
      event.preventDefault();

      // Emits the event
      this.$emit("add-todo", {
        title: this.title,
        description: this.description,
        complete: false,
      });

      // Clears the inputs
      this.title = "";
      this.description = "";

      // Sets the focus to the title input field
      this.$refs.title.focus();
    },
  },
};
</script>

<style lang="scss" scoped>
form {
  margin: 4px 8px;
  display: flex;
  border-radius: 12px;
  align-items: center;
  box-shadow: 4px 4px 12px rgba(0, 0, 0, 0.125),
    -4px -4px 12px rgba(255, 255, 255, 1);

  input,
  button {
    outline: none;
  }

  label {
    width: 100%;

    input {
      padding: 4px 8px;
      font-size: 16px;
      width: 100%;
      border: 1px solid #fff;

      &:nth-child(1) {
        border-radius: 12px 0 0 0;
      }
      &:nth-child(2) {
        border-radius: 0 0 0 12px;
      }
    }
  }

  button {
    border: none;
    border-radius: 0 12px 12px 0;
    padding: 22px 16px;
    font-size: 16px;
    color: #fff;
    background: linear-gradient(90deg, #cb2d3e, #ef473a);
  }
}
</style>
