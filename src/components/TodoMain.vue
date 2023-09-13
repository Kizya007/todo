<template>
  <li class="todo">
    <div class="todo-text">
      <p class="todo-text__title">Dinner</p>
      <p class="todo-text__time">Today at 8:00 PM</p>
    </div>
    <div class="todo-icons">
      <circleIcon />
      <garbageIcon />
    </div>
  </li>
</template>

<script>
import circleIcon from "../assets/icon/circleIcon.vue";
import garbageIcon from "../assets/icon/garbageIcon.vue";

export default {
  name: "TodoMain",
  components: {
    circleIcon,
    garbageIcon,
  },
};
</script>

<style lang="scss">
@import "../assets/todo.scss";
</style>
