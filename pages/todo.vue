<template>
  <div class="container">
    <h1 class="title">My To Do List</h1>
    <to-do-list :todos="todos" />
    <br />
  </div>
</template>

<script>
import ToDoList from "~/components/ToDoList.vue";

export default {
  components: {
    ToDoList
  },
  data() {
    return {
      todos: {
        type: Array
      }
    };
  },
  asyncData(ctx) {
    return {
      todos: [
        {
          id: "1",
          title: "A",
          completed: true
        },
        {
          id: "2",
          title: "B",
          completed: false
        },
        {
          id: "3",
          title: "C",
          completed: false
        }
      ]
    };
  }
};
</script>