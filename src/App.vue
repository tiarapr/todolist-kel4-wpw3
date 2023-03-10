<script setup>
import SideBar from './components/SideBar.vue'
import TaskList from './components/TaskList.vue'
import Notif from './components/Notification.vue'
import { ref } from 'vue'

const maxTitleLength = 20
const maxDescLength = 150
const titleInput = ref('')
const descInput = ref('')
const tasks = ref([])
const notifData = ref([false, '', true])

function notification(message, notifStatus) {
  notifData.value[1] = message
  notifData.value[2] = notifStatus
  notifData.value[0] = true
  setTimeout(() => {
    notifData.value[0] =false
  }, 3000)
}

function formValidation() {
  const title = titleInput.value
  const description = descInput.value
  if (title && description) {
    submitForm({ title, description })
    titleInput.value = ''
    descInput.value = ''
  } else
    notification('Tugas gagal ditambahkan', false)
}

function submitForm(task) {
  addNewTask(task) 
}

function addNewTask(task) {
  tasks.value.push(task)
  notification('Tugas berhasil ditambahkan!', true)
}

function removeTask(index) {
  tasks.value.splice(index, 1)
  notification('Tugas berhasil dihapus!', true)
}
</script>

<template>
  <Notif :notifData="notifData" />
  <SideBar v-model:titleInput="titleInput" v-model:descInput="descInput" :formValidation="formValidation" :submitForm="submitForm" :maxTitleLength="maxTitleLength" :maxDescLength="maxDescLength" />
  <TaskList :tasks="tasks" :removeTask="removeTask" />
</template>
