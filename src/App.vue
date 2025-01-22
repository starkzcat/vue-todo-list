<script setup>
import { useTemplateRef, reactive } from "vue";

const inputField = useTemplateRef("input-field");

const todo = reactive({
  title: "",
  isDone: false,
});
</script>

<template>
  <input
    ref="input-field"
    v-model="todo.title"
    type="text"
    placeholder="Add new todo..."
  />
  <button>Add</button>

  <div>
    <ul>
      <li>Eat</li>
      <li>Sleep</li>
      <li>Gym</li>
    </ul>
  </div>

  <span>{{ todo.title }}</span>
</template>

<style scoped></style>
