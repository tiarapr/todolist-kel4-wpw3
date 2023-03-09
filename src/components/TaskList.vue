<script setup>
import Task from './Task.vue'

defineProps({
  tasks: Array,
  removeTask: Function
})
</script>

<template>
  <div class="listTask">
    <h1>List Tasks</h1>
    <div class="cards">
      <Task :tasks="tasks" :removeTask="removeTask" />
    </div>
  </div>
</template>

<style scoped>
.listTask {
  flex-grow: 3;
}

.listTask h1 {
  /* text-align: center; */
  margin-bottom: 1em;
  color: #ff8906;
}

.cards {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 1em;
}
</style>
