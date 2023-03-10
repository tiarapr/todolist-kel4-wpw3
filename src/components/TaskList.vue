<script setup>
import Task from './Task.vue'

defineProps({
  tasks: Array,
  removeTask: Function,
  editTask: Function
})
</script>

<template>
  <div class="listTugas">
    <h1>Daftar Tugas</h1>
    <div class="cards" v-if="tasks.length">
      <Task :tasks="tasks" :removeTask="removeTask" :editTask="editTask" />
    </div>
    <div class="cardNotFound" v-else>
      <p>Anda belum memiliki tugas.</p>
      <p>Silahkan buat tugas baru terlebih dahulu!</p>
    </div>
  </div>
</template>

<style scoped>
.listTugas {
  flex-grow: 3;
  position: relative;
}

.listTugas h1 {
  text-align: center;
  margin-bottom: 1em;
  color: #fffffe;
}

.listTugas .cards {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 1em;
}

.listTugas .cardNotFound {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%); 
  text-align: center;
  color: #a7a9be;
  font-weight: 300;
  display: flex;
  flex-direction: column;
  grid-gap: 0.4em;
}
</style>
