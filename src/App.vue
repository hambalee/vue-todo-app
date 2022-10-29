<script setup lang="ts">
import { ref } from "vue";

const todoValue = ref("eating");

const todoList = ref(["travel", "coding", "running"]);

const onAddTodo = (newTodo: string) => {
  todoList.value.push(newTodo);
};

const onRemoveTodo = (index: number) => {
  // todoList.value.splice(index, 1);
  const newTodoList = todoList.value.filter((val, i) => i != index);
  todoList.value = [...newTodoList];
};
</script>

<template>
  <h1 class="title">Todo app</h1>
  <div class="todo-wrapper">
    <input v-model="todoValue" class="my-input" type="text" />
  </div>
  <div class="todo-wrapper">
    <ul>
      <li v-for="(todo, index) of todoList" :key="index">
        {{ todo }}

        <button @click="onRemoveTodo(index)">X</button>
      </li>
    </ul>
  </div>

  <div class="todo-wrapper">
    <button @click="onAddTodo(todoValue)">Add Todo</button>
  </div>
</template>

<style scoped>
.title {
  text-align: center;
}

.my-input,
button {
  font-size: 24px;
}

.todo-wrapper {
  display: flex;
  justify-content: center;
}

ul > li {
  font-size: 24px;
}
</style>
