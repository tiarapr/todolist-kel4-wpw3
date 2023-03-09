<script setup>
defineProps({
  titleInput: String,
  descInput: String,
  submitForm: Function
})

const emit = defineEmits(['update:titleInput', 'update:descInput'])

const maxTitleLength = 20
const maxDescLength = 100
</script>

<template>
  <div class="formInput">
    <form>
      <h1>Add Task</h1>
      <div>
        <label for="title">Title</label>
        <input type="text" 
        placeholder="Title" 
        id="title" :maxlength="maxTitleLength" :class="{ inputError: titleInput.length === maxTitleLength }" :value="titleInput" @input="$emit('update:titleInput', $event.target.value)" 
        />
      </div>
      <div>
        <label for="description">Description</label>
        <textarea 
        placeholder="Description" 
        id="description" :maxlength="maxDescLength" :class="{ inputError: descInput.length === maxDescLength }" :value="descInput" @input="$emit('update:descInput', $event.target.value)">
        </textarea>
      </div>
    </form>
    <button type="button" @click="submitForm">Add</button>
  </div>
</template>

<style scoped>
.formInput {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  padding: 1.5em 2em;
  background-color: #2e2e2e;
  color: #ff8906;
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
  color: #fff;
  cursor: pointer;
}

.formInput input, .formInput textarea {
  background-color: #fff;
  padding: 0.5em 1em;
  color: #2e2e2e;
  font-family: inherit;
  font-size: 1em;
  border: 2px solid #fff;
  border-radius: 0.25em;
  outline: none;
  box-sizing: border-box;
}

.formInput textarea {
  height: 10em;
  resize: none;
}

.formInput .inputError {
  color: #e53170;
  border-color: #e53170;
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
