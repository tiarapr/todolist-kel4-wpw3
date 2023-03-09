<template>
  <div class="formInput">
    <form>
      <h1>Add Task</h1>
      <div>
        <label for="title">Title</label>
        <input type="text" 
        placeholder="Title" 
        id="title" 
        v-model.trim="newTitleTodo" 
        @keydown.enter="addNewTitleTodo" 
        @keydown.tab.prevent="addNewTitleTodo"
        @keydown.delete="removeTodo" 
        />
      </div>
      <div>
        <label for="desc">Description</label>
        <textarea 
        placeholder="Description Task" 
        id="desc"
        v-model.trim="newDescTodo" 
        @keydown.enter="addNewDescTodo" 
        @keydown.tab.prevent="addNewDescTodo"
        @keydown.delete="removeTodo" 
        >
        </textarea>
      </div>
    </form>
    <button type="button" @click="addTodo">Add Task</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTitleTodo: "",
      newDescTodo: "",
      todos: [],
    };
  },
  methods: {
    addTodo() {
      this.todos.push(this.newTitleTodo, newDescTodo);
      this.newTitleTodo = "";
      this.newDescTodo = "";
    },
    removeTodo(index) {
      this.todos.splice(index, 1);
    },
  },
};
</script>

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

.formInput input, .formInput textarea {
  background-color: #0f0e17;
  padding: 0.5em 1em;
  color: #fffffe;
  font-family: inherit;
  font-size: 1em;
  border: none;
  border-radius: 0.25em;
  outline: none;
}

.formInput textarea {
  height: 10em;
  resize: none;
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
