<script setup>
import SideBar from './components/SideBar.vue'
import TaskList from './components/TaskList.vue'
import { ref } from 'vue'

const tasks = ref([])
const titleInput = ref('')
const descInput = ref('')

function submitForm() {
  const title = titleInput.value
  const desc = descInput.value
  if (title && desc) {
    addNewTask(title, desc)
    titleInput.value = ''
    descInput.value = ''
  }
}

function addNewTask(title, desc) {
  tasks.value.push({
    title: title,
    description: desc
  }) 
}

function removeTask(index) {
  tasks.value.splice(index, 1)
}
</script>

<template>
  <SideBar v-model:titleInput="titleInput" v-model:descInput="descInput" :submitForm="submitForm" />
  <TaskList :tasks="tasks" :removeTask="removeTask" />
</template>
