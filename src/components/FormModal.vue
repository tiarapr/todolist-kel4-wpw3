<script setup>
defineProps({
  isActiveModal: Boolean,
  modalToggle: Function,
  taskIndex: Number,
  editTitleInput: String,
  editDescInput: String,
  formValidation: Function,
  maxTitleLength: Number,
  maxDescLength: Number
})

const emit = defineEmits(['update:editTitleInput', 'update:editDescInput'])
</script>

<template>
  <div class="modal" :style="{ display: isActiveModal ? 'block' : 'none' }">
    <form @submit.prevent="formValidation(editTitleInput, editDescInput, taskIndex)">
      <h1>Ubah Tugas</h1>
      <div>
        <label for="modalJudul">Judul <span class="charInfo">- {{ maxTitleLength - editTitleInput.length }} karakter tersisa</span></label>
        <input type="text" placeholder="Judul" id="modalJudul" :maxlength="maxTitleLength" :class="{ inputError: editTitleInput.length === maxTitleLength }" :value="editTitleInput" @input="$emit('update:editTitleInput', $event.target.value)" @keydown.enter.prevent="formValidation(editTitleInput, editDescInput, taskIndex)" />
      </div>
      <div>
        <label for="modalDeskripsi">Deskripsi <span class="charInfo">- {{ maxDescLength - editDescInput.length }} karakter tersisa</span></label>
        <textarea placeholder="Deskripsi" id="modalDeskripsi" :maxlength="maxDescLength" :class="{ inputError: editDescInput.length === maxDescLength }" :value="editDescInput" @input="$emit('update:editDescInput', $event.target.value)" @keydown.enter.prevent="formValidation(editTitleInput, editDescInput, taskIndex)"></textarea>
      </div>
      <button type="submit">Ubah</button>
    </form>
    <div class="modalBackground" @click="modalToggle"></div>
  </div>
</template>

<style scoped>
.modal {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100vh;
  z-index: 1;
}

.modal .modalBackground {
  width: 100%;
  height: 100vh;
  background-color: rgba(0, 0, 0, 0.5);
}

.modal form {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background-color: #fffffe;
  padding: 2em;
  border-radius: 0.5em;
  display: grid;
  grid-row-gap: 1em;
}

.modal h1 {
  color: #0f0e17;
  text-align: center;
}

.modal div {
  display: grid;
  grid-row-gap: 0.3em;
}

.modal label {
  font-weight: bold;
  color: #0f0e17;
  cursor: pointer;
}

.modal .charInfo {
  font-weight: 300;
  color: #0f0e17;
}

.modal input, .modal textarea {
  background-color: #0f0e17;
  padding: 0.5em 1em;
  color: #fffffe;
  font-family: inherit;
  font-size: 1em;
  border: none;
  border-radius: 0.25em;
  outline: 2px solid transparent;
  box-sizing: border-box;
}

.modal textarea {
  height: 10em;
  resize: none;
}

.modal .inputError {
  color: #e53170;
  outline-color: #e53170;
}

.modal button {
  background-color: #ff8906;
  color: #fffffe;
  border: none;
  font-size: 1.2em;
  font-weight: bold;
  font-family: inherit;
  padding: 0.5em;
  border-radius: 0.25em;
  cursor: pointer;
}
</style>
