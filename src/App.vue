<script setup>
import { ref } from 'vue'
import ListForm from './assets/ListForm.vue'
import ListLoop from './assets/ListLoop.vue'
</script>

<template>
  <div>
    <h1>Get in. We're going shopping.</h1>
  </div>

  <ListForm />

  <div class="listcontainer">
    <ListLoop />
  </div>
</template>

<style scoped></style>
