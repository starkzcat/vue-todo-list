<script setup>
import { ref } from "vue";

let count = ref(0);
</script>

<template>
  <h3>{{ count }}</h3>
  <button @click="count++">+</button>
  <button @click="count--">-</button>
</template>

<style scoped></style>
