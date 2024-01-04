<template>
  <div class="listcard" v-for="list in lists" :key="list.id">
    <li class="listTitle">{{ list.title }}</li>
    <NewItem />
    <button type="submit" id="editbutton">EDIT</button>
    <button type="submit" id="deletebutton">DELETE</button>
  </div>
</template>

<script setup>
import { ref } from 'vue'

import NewItem from './NewItem.vue'

const props = defineProps({ list: Object })

const lists = ref([])

console.log(lists)

const listAPI = 'http://localhost:3000/lists/'

// GET REQUEST TO PULL LISTS FROM DATABASE OF LISTS //
fetch(listAPI, {
  method: 'GET',
  headers: { 'Content-Type': 'application/json' }
})
  .then((response) => response.json())
  .then((response) => (lists.value = response))
</script>
