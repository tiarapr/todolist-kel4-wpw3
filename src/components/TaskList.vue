<script setup>
import Task from './Task.vue'

defineProps({
  data: Array
})
</script>

<template>
  <div class="listTugas">
    <h1>List Task</h1>
    <div class="cards">
      <Task :data="data" />
    </div>
  </div>
</template>

<style scoped>
.listTugas {
  flex-grow: 3;
}

.listTugas h1 {
  text-align: center;
  margin-bottom: 1em;
  color: #fffffe;
}

.cards {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 1em;
}
</style>
