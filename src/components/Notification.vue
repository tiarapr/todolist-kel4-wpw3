<script setup>
defineProps({
  notifData: Array
})
</script>

<template>
  <div class="notification" :class="{ notifActive: notifData[0] }" :style="{ backgroundColor: notifData[2] ? '#8bd3dd' : '#e53170', color: notifData[2] ? '#0f0e17' : '#fffffe' }">
    <p v-text="notifData[1]"></p>
  </div>
</template>

<style scoped>
.notification {
  position: absolute;
  top: -5em;
  right: 2em;
  padding: 0.5em 1em;
  border-radius: 0.3em;
  outline: 2px solid transparent;
  z-index: 3;
  transition: all 300ms;
}

.notification.notifActive {
  top: 1em;
}

.notification:hover {
  outline-color: #ff8906;
}

.notification p {
  font-weight: bold;
}
</style>
