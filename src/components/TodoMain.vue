<template>
  <li class="todo">
    <div class="todo-text">
      <p class="todo-text__title">{{ item.title }}</p>
      <p class="todo-text__time">{{ item.date }}</p>
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
  props: {
    item: Object,
  },
  components: {
    circleIcon,
    garbageIcon,
  },
};
</script>

<style lang="scss">
@import "../assets/todo.scss";
</style>
