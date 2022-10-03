<script setup>
import { ref } from "vue";

const todoList = ref([
  { name: "算数", status: true },
  { name: "国語", status: false },
]);
const newTodoName = ref("");

const addTodo = () => {
  todoList.value.push({ name: newTodoName.value, status: false });
  newTodoName.value = "";
};

const done = (todo) => {
  todo.status = true;
};

const undone = (todo) => {
  todo.status = false;
};
</script>

<template>
  <dev>TodoList</dev>
  <div v-for="todo in todoList" :key="todo.name">
    <div class="todo">
      <div class="name">やること： {{ todo.name }}</div>
      <div v-if="todo.status" class="status">
        　完了
        <button @click="undone(todo)">未完了にする</button>
      </div>
      <div v-else class="status">
        　未完了
        <button @click="done(todo)">完了にする</button>
      </div>
    </div>
  </div>
  <div>
    <label>
      やること
      <input v-model="newTodoName" type="text" />
    </label>
    <button @click="addTodo">add</button>
  </div>
</template>

<style>
.todo {
  display: flex;
  justify-content: center;
}
</style>