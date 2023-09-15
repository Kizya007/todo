<template>
  <li class="todo">
    <div class="todo-text">
      <p class="todo-text__title">{{ item.title }}</p>
      <p class="todo-text__time">{{ item.date }}</p>
    </div>
    <div class="todo-icons">
      <circleIcon />
      <garbageIcon @click="deleteTodo" />
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
  emits: [
    'deleteTodo',
  ],
  components: {
    circleIcon,
    garbageIcon,
  },
  setup(props,context) {
    function deleteTodo() {
      context.emit('deleteTodo', props.item.title)
    }
    return {
      deleteTodo,
    }
  },
};
</script>

<style lang="scss">
@import "../assets/todo.scss";
</style>
