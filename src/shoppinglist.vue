<template>
  <div v-for="list in lists" :key="list.id">
    <h1>{{ list.title }}</h1>

    <li v-for="item in list.items" :key="item.id">
      {{ item.itemName }}
      {{ console.log(item.itemName) }}
    </li>
  </div>
</template>
<script>
import { ref } from 'vue'

const lists = ref([])

fetch('http://localhost:3000/lists/', {
  method: 'GET',
  headers: { 'Content-Type': 'application/json' }
})
  .then((res) => res.json())
  .then((data) => (lists.value = data))
</script>
