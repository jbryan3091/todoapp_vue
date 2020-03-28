<template>
  <div class="container">
    <h1 class="title">spotlight 💡</h1>
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
    return {};
  },
  asyncData(ctx) {
    return {};
  }
};
</script>