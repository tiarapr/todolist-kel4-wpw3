<script setup>
defineProps({
  tasks: Array,
  removeTask: Function,
  editTask: Function
})
</script>

<template>
  <div class="card" v-for="(task, index) in tasks">
    <h2 v-text="task.title"></h2>  
    <p v-text="task.description"></p>
    <div class="taskOption">
      <div class="iconPosition">
        <span @click="removeTask(index)">
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" stroke="#e53170" stroke-linecap="round" stroke-linejoin="round" class="feather feather-trash-2">
            <polyline points="3 6 5 6 21 6"></polyline>
            <path d="M19 6v14a2 2 0 0 1-2 2H7a2 2 0 0 1-2-2V6m3 0V4a2 2 0 0 1 2-2h4a2 2 0 0 1 2 2v2"></path>
            <line x1="10" y1="11" x2="10" y2="17"></line>
            <line x1="14" y1="11" x2="14" y2="17"></line>
          </svg>
        </span>
        <span @click="editTask(index)">
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" stroke="#2cb67d" stroke-linecap="round" stroke-linejoin="round">
            <path d="M17 3a2.828 2.828 0 1 1 4 4L7.5 20.5 2 22l1.5-5.5L17 3z"></path>
          </svg>
        </span>
      </div>
    </div>
  </div>
</template>

<style scoped>
.card {
  display: flex;
  flex-direction: column;
  background-color: #fffffe;
  padding: 1em;
  position: relative;
  overflow: hidden;
}

.card svg {
  fill: none;
  stroke-width: 2;
  width: 22px;
  height: 22px;
  opacity: 0.75;
  transition: opacity 200ms;
}

.card svg:hover {
  opacity: 1;
}

.card h2 {
  line-height: 1;
  color: #0f0e17;
  margin-bottom: 0.5em;
}

.card p {
  color: #2e2f3e;
  font-weight: 300;
}

.card .taskOption {
  position: absolute;
  background-color: #0f0e17;
  top: 0;
  right: -2em;
  height: 100%;
  transition: right 500ms;
}

.card:hover .taskOption {
  right: 0;
}

.card .iconPosition {
  display: flex;
  flex-direction: column;
  position: relative;
  top: 50%;
  transform: translateY(-50%);
}

.card .taskOption span {
  display: flex;
  padding: 0.6em;
  cursor: pointer;
}
</style>
