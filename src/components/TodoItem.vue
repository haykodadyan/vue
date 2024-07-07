<script setup>
import {inject} from "vue";

defineProps({
  id: Number,
  text: String
})

const {todos} = inject('todos')

const handleCheckboxClick = (id) => {
todos.value.forEach(elem => {
    if (elem.id === id) {
      elem.isDone = !elem.isDone
    }
  })
}

const handleDelete = (id) => {
  todos.value = todos.value.filter((elem) => elem.id !== id)
}

</script>

<template>
  <div class="todo-item">
    <h3>{{text}}</h3>
    <div class="todo-props-block">
      <input @click="() => handleCheckboxClick(id)" class="check-button" type="checkbox">
      <button @click="() => handleDelete(id)">Delete</button>
      <button>Edit</button>
    </div>
  </div>
</template>

<style scoped>
.todo-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex: 1;
}
.check-button {
  //height: fit-content;
}
.todo-props-block {
  display: flex;
  justify-content: space-around;
  width: 10rem;
}
h3 {
  width: 20rem;
}
</style>