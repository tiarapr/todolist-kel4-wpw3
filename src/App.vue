<script setup>
import SideBar from './components/SideBar.vue'
import TaskList from './components/TaskList.vue'
import { ref } from 'vue'

// const data = ref([
//   {
//     judul: "Judul Pertama",
//     deskripsi: "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua."
//   },
//   {
//     judul: "Judul Kedua",
//     deskripsi: "Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur."
//   }
// ])
</script>

<template>
  <SideBar />
  <TaskList :data="data" />
</template>
