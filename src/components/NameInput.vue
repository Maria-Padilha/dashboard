<template>
  <h2 class="mb-5">Bem vindo, <input type="text" placeholder="Seu nome" v-model="name"></h2>
</template>

<script setup>
import { onMounted, ref, watch } from 'vue';

const name = ref('');
watch(name, (newName) => {
    localStorage.setItem('name', newName)
})
onMounted(() => {
    name.value = localStorage.getItem('name') || '';
})
</script>

<style scoped>
  input:focus{
    outline: none;
  }
</style>