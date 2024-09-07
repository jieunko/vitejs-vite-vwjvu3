<script setup>
import { ref } from 'vue';

const inputValue = ref('');

const todoList = ref([
  { text: 'a', done: false },
  { text: 'b', done: false },
  { text: 'c', done: false },
]);

const printInputValue = () => {
  console.log(inputValue.value);
};
const handleClickDeleteButton = (index) => {
  todoList.value.splice(index, 1);
};
const handleClickChangeButton = (index) => {
  todoList.value.splice(index, 1);
};
const handleClickButton = () => {
  todoList.value.push(inputValue.value);
  console.log(todoList.value);
};
const handleChange = (event) => {
  consloe.log(event);
  const nextValue = event.target.value;
  inputValue.value = nextValue;
};
const count = ref(0);
const increase = () => {
  count.value++;
};
const decrease = () => {
  count.value--;
};
</script>

<!-- html -->
<template>
  <p>{{ todoList }}</p>
  <h2>TODO LIST</h2>
  <div>
    <div>count : {{ count }}</div>
    <button @click="increase">+</button>
    <button @click="decrease">-</button>
  </div>
  <input v-model="inputValue" />
  <p>{{ inputValue }}</p>
  <!-- <input :value="inputValue" @change="handleChange" /> -->
  <!-- <p>{{ inputValue }}</p> -->

  <button @click="handleClickButton">OK</button>
  <div class="todo-item" v-for="(item, index) in todoList">
    <input type="checkbox" v-model="item.done" />
    <span :class="{ 'done-item': item.done }"> {{ item.text }}</span>
    <button @click="handleClickDeleteButton(index)">delete</button>
  </div>
  <!-- css 관리 위치 -->
</template>

<style scoped>
.todo-item {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  border: 1px solid gray;
}
.done-item {
  text-decoration: line-through;
}
h2 {
  color: magenta;
}
</style>
