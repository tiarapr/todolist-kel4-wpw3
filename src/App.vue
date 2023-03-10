<script setup>
import SideBar from './components/SideBar.vue'
import TaskList from './components/TaskList.vue'
import Notif from './components/Notification.vue'
import FormModal from './components/FormModal.vue'
import { ref } from 'vue'

const maxTitleLength = 20
const maxDescLength = 150
const titleInput = ref('')
const descInput = ref('')
const tasks = ref([])
const notifData = ref([false, '', true])
const isActiveModal = ref(false)
const taskIndex = ref(0)
const editTitleInput = ref('')
const editDescInput = ref('')

function notification(message, notifStatus) {
  notifData.value[1] = message
  notifData.value[2] = notifStatus
  notifData.value[0] = true
  setTimeout(() => {
    notifData.value[0] =false
  }, 3000)
}

function modalToggle() {
  isActiveModal.value = !isActiveModal.value
}

function formValidation(title, description, index = -1) {
  if (title && description)
    submitForm({ title, description }, index)
  else
    notification('Input tidak valid!', false)
}

function submitForm(task, index) {
  if (index >= 0) {
    updateTask(task, index)
    editTitleInput.value = ''
    editDescInput.value = ''
  } else {
    addNewTask(task)
    titleInput.value = ''
    descInput.value = ''
  }
}

function addNewTask(task) {
  tasks.value.push(task)
  notification('Tugas berhasil ditambahkan!', true)
}

function removeTask(index) {
  tasks.value.splice(index, 1)
  notification('Tugas berhasil dihapus!', true)
}

function editTask(index) {
  taskIndex.value = index
  editTitleInput.value = tasks.value[index].title
  editDescInput.value = tasks.value[index].description
  modalToggle()
}

function updateTask(task, index) {
  tasks.value.splice(index, 1, task)
  modalToggle()
  notification('Tugas berhasil diubah!', true)
}
</script>

<template>
  <Notif :notifData="notifData" />
  <SideBar v-model:titleInput="titleInput" v-model:descInput="descInput" :formValidation="formValidation" :submitForm="submitForm" :maxTitleLength="maxTitleLength" :maxDescLength="maxDescLength" />
  <TaskList :tasks="tasks" :removeTask="removeTask" :editTask="editTask" />
  <FormModal :isActiveModal="isActiveModal" :modalToggle="modalToggle" :taskIndex="taskIndex" v-model:editTitleInput="editTitleInput" v-model:editDescInput="editDescInput" :formValidation="formValidation" :maxTitleLength="maxTitleLength" :maxDescLength="maxDescLength" />
</template>
