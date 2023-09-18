<template>
  <li class="todo">
    <div class="todo-text" v-if="isEdit === false">
      <p class="todo-text__title">{{ item.title }}</p>
      <p class="todo-text__time">{{ item.date }}</p>
    </div>
    <div v-if="isEdit === true">
      <input type="text" placeholder="todo name" v-model="localValue" />
    </div>
    <div class="todo-icons">
      <circleIcon @click="edit" v-if="isEdit === false" />
      <button @click="save" v-if="isEdit === true">Save</button>
      <garbageIcon @click="deleteTodo" />
    </div>
  </li>
</template>

<script>
import { ref } from "vue";
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
  setup(props, context) {
    const isEdit = ref(false);
    const localValue = props.item ? ref(props.item.title) : "";

    function save() {
      context.emit("save", {
        title: props.item.title,
        newTitle: localValue,
      });
    }

    function deleteTodo() {
      context.emit("deleteTodo", props.item.title);
    }
    function edit() {
      isEdit.value = true;
    }
    return {
      deleteTodo,
      edit,
      isEdit,
      save,
      localValue,
    };
  },
};
</script>

<style lang="scss">
@import "../assets/todo.scss";
</style>
