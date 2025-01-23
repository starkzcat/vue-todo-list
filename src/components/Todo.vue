<script setup>
const { tasks } = defineProps(["tasks"]);
const emit = defineEmits(["delete"]);
</script>

<template>
  <div>
    <ul>
      <li v-for="task in tasks" :key="task.id">
        <input
          v-model="task.completed"
          type="checkbox"
          :checked="task.completed"
          :id="task.id"
        />
        <label :for="task.id">
          <span :class="{ done: task.completed }">{{ task.title }}</span>
        </label>
        <button @click="emit('delete', task.id)">
          <i class="fa fa-trash-o"></i>
        </button>
      </li>
    </ul>
  </div>
</template>

<style scoped>
.done {
  text-decoration: line-through;
}

i {
  color: red;
  font-size: 16px;
}

button {
  margin-left: 4px;
}
</style>
