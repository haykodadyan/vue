<script setup>
import {inject, ref} from "vue";
import TodoItem from "./TodoItem.vue";
const {todos} = inject('todos')

</script>

<template>
  <div class="list" v-for="item of todos" :key="item.id">
    <TodoItem
        :text="item.text"
        :id="item.id"
    />
  </div>
</template>

<style scoped>
.list {
  display: flex;
  justify-content: center;
  width: 40vw;
  top: 0;
}
</style>