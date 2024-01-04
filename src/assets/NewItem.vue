<template>
  <div>
    <form>
      <input type="text" placeholder="New Item" />
      <button type="submit">Save</button>
    </form>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const newItem = ref('')

const addItem = ref(false)

const addAnItem = (e) => {
  addingItem.value = e
}

const resetItem = () => {
  newItem.value = ''
}

const listAPI = 'http://localhost:3000/lists/'

const props = defineProps({ list: Object })
const emit = defineEmits(['itemAdded'])

const addNewItem = () => {
  fetch(listAPI + props.list.id, {
    method: 'PATCH',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify({
      title: props.list.title,
      items: [
        ...props.list.items,
        {
          id: props.list.items.length + 1,
          itemName: newItem.value,
          purchased: false
        }
      ],
      updatedAt: new Date()
    })
  })
    .then((res) => res.json())
    .then((addedItem) => {
      emit('itemAdded', addeditem)
      resetItem()
    })
}
</script>
