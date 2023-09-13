<template>
  <div class="container">
    <div class="header">
      <img class="header-img" src="./assets/img/todoImg.png" alt="" />
      <div class="header-date">
        <p class="header-date__week">Thur 9</p>
        <p class="header-date__time">6:23</p>
      </div>
    </div>
    <div class="todo-content">
      <input class="todo-content__input" type="text" placeholder="Note" />
      <div class="todo-content__icon">
        <plusIcon />
        <arrowBottom />
      </div>
    </div>
    <ul class="todo-list">
      <TodoMain />
      <TodoMain />
      <TodoMain />
      <TodoMain />
    </ul>
  </div>
</template>

<script>
import TodoMain from "./components/TodoMain.vue";
import plusIcon from "./assets/icon/plusIcon.vue";
import arrowBottom from "./assets/icon/arrowBottom.vue";

export default {
  name: "App",
  components: {
    TodoMain,
    plusIcon,
    arrowBottom,
  },
};
</script>

<style lang="scss">
@import "./assets/App.scss";
@import url("https://fonts.googleapis.com/css2?family=Inter:wght@100;200;300;500;600;700&family=Russo+One&display=swap");
</style>
