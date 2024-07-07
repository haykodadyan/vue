<script setup>
import {inject, onMounted, ref} from "vue";

const input = ref('')
const mounted = ref(false)
const {todos} = inject('todos')

const handleInputChange = (e) => {
  input.value = e.target.value
}
const handleClick = () => {
  if (input.value.trim() !== '') {
    todos.value.push({
      id: Math.round(Math.random() * 10000000),
      text: input.value,
      isDone: false
    })
  }
  input.value = ''
}

const deleteCheckedTodos = () => {
  todos.value = todos.value.filter(elem => !elem.isDone)
}

onMounted(() => {
  setTimeout(() => {
    mounted.value = true
  }, 100)
})
</script>

<template>
    <div :class="{'fade-in': mounted}" class="header">
      <h2>Welcome to TodoList!</h2>
      <div class="input-and-button">
        <input
            v-model="input"
            @input="(e) => handleInputChange(e)"
            type="text"
            placeholder="What's new today...">
        <button @click="handleClick">Add todo</button>
        <button @click="deleteCheckedTodos" v-if="todos.some(elem => elem.isDone)">Delete Ckecked</button>
      </div>
    </div>
</template>

<style scoped>
  * {
    font-family: "Futura Thin";
  }
  input:focus {
    outline: none;
  }
  .input-and-button {
    display: flex;
    width: 100vw;
    justify-content: center;
  }
  .header {
    opacity: 0;
    position: sticky;
    top: 0;
    background-color: #2f2f2f;
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  .fade-in {
    transition: opacity 1.6s ease-in;
    opacity: 1;
  }

</style>