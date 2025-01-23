<script setup>
import { computed, ref } from "vue";
import Todo from "./components/Todo.vue";

let id = 0;
const hideCompleted = ref(false);
const newTask = ref("");
const tasks = ref([
  {
    id: id++,
    title: "Eat",
    completed: false,
  },
  {
    id: id++,
    title: "Sleep",
    completed: false,
  },
  {
    id: id++,
    title: "Gym",
    completed: true,
  },
]);
const filteredTasks = computed(() => {
  return hideCompleted.value
    ? tasks.value.filter((task) => !task.completed)
    : tasks.value;
});

function addTodo() {
  tasks.value.push({ id: id++, title: newTask.value, completed: false });

  newTask.value = "";
}

function deleteTodo(id) {
  tasks.value = tasks.value.filter((task) => task.id !== id);
}

function clearTasks() {
  tasks.value = [];
}
</script>

<template>
  <h1>Todo List App</h1>
  <form @submit.prevent="addTodo">
    <input type="text" placeholder="Add task" v-model="newTask" />
    <button>Add</button>
  </form>
  <Todo :tasks="filteredTasks" @delete="(id) => deleteTodo(id)" />

  <button @click="() => (hideCompleted = !hideCompleted)">
    {{ hideCompleted ? "Show All" : "Hide Done" }}
  </button>
  <button @click="clearTasks">Clear All</button>
</template>

<style scoped></style>
