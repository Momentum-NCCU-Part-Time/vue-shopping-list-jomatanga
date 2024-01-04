<template>
  <form id="listForm" @submit.prevent="createList">
    <input v-model="listName" type="text" id="listName" placeholder="Store Name" />
    <button type="submit" id="submitlist">NEW LIST</button>
  </form>
</template>

<script setup>
import { ref } from 'vue'

const listName = ref('')

const listAPI = 'http://localhost:3000/lists/'

// PICK UP HERE //

const createList = () => {
  console.log(listName.value)
  const newList = { title: listName.value }
  const title = listName.value
  const items = []

  fetch(listAPI, {
    method: 'POST',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify({ title, items, updatedAt: new Date() })
  })
    .then((res) => res.json())
    .then(
      (data) => console.log(data)
      // or whatever you need to do
    )
}
</script>
