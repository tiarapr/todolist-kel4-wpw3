<script setup>
defineProps({
  titleInput: String,
  descInput: String,
  formValidation: Function,
  submitForm: Function,
  maxTitleLength: Number,
  maxDescLength: Number
})

const emit = defineEmits(['update:titleInput', 'update:descInput'])
</script>

<template>
  <div class="formInput">
    <form @submit.prevent="formValidation">
      <h1>Buat Tugas</h1>
      <div>
        <label for="judul">Judul <span class="charInfo">- {{ maxTitleLength - titleInput.length }} karakter tersisa</span></label>
        <input type="text" placeholder="Judul" id="judul" :maxlength="maxTitleLength" :class="{ inputError: titleInput.length === maxTitleLength }" :value="titleInput" @input="$emit('update:titleInput', $event.target.value)" @keydown.enter.prevent="formValidation" />
      </div>
      <div>
        <label for="deskripsi">Deskripsi <span class="charInfo">- {{ maxDescLength - descInput.length }} karakter tersisa</span></label>
        <textarea placeholder="Deskripsi" id="deskripsi" :maxlength="maxDescLength" :class="{ inputError: descInput.length === maxDescLength }" :value="descInput" @input="$emit('update:descInput', $event.target.value)" @keydown.enter.prevent="formValidation"></textarea>
      </div>
    </form>
    <button type="button" @click="formValidation">Kirim</button>
  </div>
</template>

<style scoped>
.formInput {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  padding: 1.5em 2em;
  background-color: #fffffe;
  color: #0f0e17;
  border-radius: 0.5em
}

.formInput h1 {
  text-align: center;
  margin-bottom: 0.5em;
}

.formInput form {
  display: grid;
  grid-row-gap: 1em;
}

.formInput div {
  display: grid;
  grid-row-gap: 0.3em;
}

.formInput label {
  font-weight: bold;
  color: #0f0e17;
  cursor: pointer;
}

.formInput .charInfo {
  font-weight: 300;
  color: #0f0e17;
}

.formInput input, .formInput textarea {
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

.formInput textarea {
  height: 10em;
  resize: none;
}

.formInput .inputError {
  color: #e53170;
  outline-color: #e53170;
}

.formInput button{
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
