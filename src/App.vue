<template>
  <div class="container">
    <div class="header">
      <img class="header-img" src="./assets/img/todoImg.png" alt="" />
      <div class="header-date">
        <p class="header-date__week">{{ nowDay }} {{ nowDate }}</p>
        <p class="header-date__time">{{ nowTime }}</p>
      </div>
    </div>
    <div class="todo-content">
      <input
        :class="['todo-content__input', { error: form.text === '' }]"
        v-model="form.text"
        type="text"
        placeholder="Note"
      />
      <div class="todo-content__icon">
        <plusIcon @click="addTodo" />
        <arrowBottom />
      </div>
    </div>
    <ul class="todo-list">
      <TodoMain
        v-for="todo in state.todos"
        :item="todo"
        :key="todo.title"
        @deleteTodo="todoDelete"
        @save="changeTodo"
      />
    </ul>
  </div>
</template>

<script>
import TodoMain from "./components/TodoMain.vue";
import plusIcon from "./assets/icon/plusIcon.vue";
import arrowBottom from "./assets/icon/arrowBottom.vue";
import { reactive } from "vue";

export default {
  name: "App",
  components: {
    TodoMain,
    plusIcon,
    arrowBottom,
  },
  setup() {
    const state = reactive({
      todos: localStorage.getItem("todos")
        ? JSON.parse(localStorage.getItem("todos"))
        : [],
    });
    const date = new Date();
    const form = reactive({
      text: "",
    });

    const weekDays = [
      "Понедельник",
      "Вторник",
      "Среда",
      "Четверг",
      "Пятница",
      "суббота",
      "Воскресенье",
    ];
    const nowDay = weekDays[date.getDay() - 1];
    const nowDate = date.getDate();
    const nowTime = date.getHours() + ":" + date.getMinutes();

    // объявляю функцию
    function addTodo() {
      // объявляю переменную которая равняется найденному значению которое возвращает функция find которую я вызвал у массива todos
      // по переданному условию, если вводимое значение в инпуте совпадает с уже существующим значением в одном из оюьектов массива
      const findTodo = state.todos.find((todo) => todo.title === form.text);
      // Проверяю наличие найденного значения в перемнной findTodo

      if (form.text === "") {
        alert("Введите значение");
        return;
      }
      if (findTodo) {
        alert("Уже такая задача есть");
      } else {
        // Обращаюсь к массиву todos и к его значению и после вызываю функцию push, с помощью которой добавляю обьект
        state.todos.push({
          title: form.text,
          date: nowTime,
        });
        localStorage.setItem("todos", JSON.stringify(state.todos));
      }
    }

    function todoDelete(value) {
      state.todos = state.todos.filter((todo) => todo.title !== value);
    }
    function changeTodo({ title, newTitle }) {
      console.log(title,newTitle);
      state.todos = state.todos.map((todo) => {
        if (todo.title === title) {
          return {
            title: newTitle,
            date: nowTime,
          };
        }
        return { ...todo };
      });
    }

    return {
      nowDay,
      nowDate,
      nowTime,
      form,
      state,
      addTodo,
      todoDelete,
      changeTodo,
    };
  },
  methods: {},
};
</script>

<style lang="scss">
@import "./assets/App.scss";
@import url("https://fonts.googleapis.com/css2?family=Inter:wght@100;200;300;500;600;700&family=Russo+One&display=swap");
</style>
