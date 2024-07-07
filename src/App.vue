<script setup>
  import Header from "./components/Header.vue";
  import Body from "./components/Body.vue";
  import {provide, ref} from "vue";

  let todos = ref([])

  provide('todos', {
    todos
  })
</script>

<template>
  <div class="wrapper">
    <Header/>
    <Body/>
  </div>
</template>

<style scoped>
.wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>