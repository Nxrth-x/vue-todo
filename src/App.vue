<template>
  <div>
    <h1 class="title">Todo list</h1>
    <todo-form @add-todo="addTodo" />
    <todo
      v-for="(todo, index) in todos"
      :info="todo"
      :index="index"
      v-bind:key="todo"
      @set-complete="setComplete"
    />
  </div>
</template>

<script>
import Todo from "./components/todo.vue";
import TodoForm from "./components/todo-form.vue";

export default {
  name: "App",
  components: {
    Todo,
    TodoForm,
  },
  data: () => ({
    todos: [],
  }),
  mounted() {
    this.todos = JSON.parse(localStorage.getItem("_todoList") || "[]");
  },
  methods: {
    addTodo(value) {
      this.todos.push(value);
    },
    setComplete(value, index) {
      this.todos[index].complete = value;
    },
  },
  watch: {
    todos: {
      handler: function(_, val) {
        localStorage.setItem("_todoList", JSON.stringify(val));
      },
      deep: true,
    },
  },
};
</script>
<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@400;700&display=swap");

* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  font-family: "Poppins", sans-serif;
}

body {
  background: #f0f0f0;
}

.title {
  font-size: 32px;
  background: linear-gradient(90deg, #cb2d3e, #ef473a);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  text-align: center;
}
</style>
