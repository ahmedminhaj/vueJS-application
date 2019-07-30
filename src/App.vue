<template>
  <div id="app">
    <Header />
    <AddTodo v-on:add-todo="addTodo" />
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" v-on:edit-todo="updateTodo" />
  </div>
</template>

<script>
import Header from "./components/layout/Header";
import Todos from "./components/Todos";
import AddTodo from "./components/AddTodo";

export default {
  name: "app",
  components: {
    Header,
    Todos,
    AddTodo
  },
  data() {
    return {
      todos: [
        {
          id: 1,
          title: "Make breakfast",
          time: Date(),
          completed: false
        },
        {
          id: 2,
          title: "Get ready for work",
          time: Date(),
          completed: false
        }
      ]
    };
  },
  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => todo.id != id);
    },
    addTodo(newTodo) {
      this.todos = [...this.todos, newTodo];
    },
    updateTodo(id) {
      this.todos[
        this.todos.findIndex(todo => todo.title === id.oldTitle)
      ].title = id.title;
    }
  }
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}
.btn {
  display: inline-block;
  border: none;
  background: #555;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}
.btn:hover {
  background: #666;
}
</style>
