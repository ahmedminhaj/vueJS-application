<template>
  <div class="todo-item" v-bind:class="{'is-completed':todo.completed}">
    <p>
      <input type="checkbox" v-on:change="markComplete" />
      {{ todo.title }}
      <br />
      {{todo.time}}
      <button @click="$emit('edit-todo', todo.id)" class="edit">Edit</button>
      <button @click="$emit('del-todo', todo.id)" class="del">X</button>
    </p>
  </div>
</template>

<script>
export default {
  name: "Todoitem",
  props: ["todo"],
  methods: {
    markComplete() {
      this.todo.completed = !this.todo.completed;
    }
  }
};
</script>

<style scoped>
.todo-item {
  background: #f4f4f4;
  padding: 10px;
  border-bottom: 1px #ccc dotted;
}

.is-completed {
  background: mediumseagreen;
  text-decoration: line-through;
}

.del {
  background: #ff0000;
  color: #fff;
  border: none;
  padding: 5px 8px;
  border-radius: 50%;
  cursor: pointer;
  float: right;
}
.edit {
  background: royalblue;
  color: #fff;
  border: none;
  padding: 7px 10px;
  border-radius: 50%;
  cursor: pointer;
  float: right;
}
</style>

