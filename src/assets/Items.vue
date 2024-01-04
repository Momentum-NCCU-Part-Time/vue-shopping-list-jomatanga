<template>
  <ul>
    <li v-for="item in items" :key="item.id">
      {{ list.items.itemName }}
    </li>
  </ul>
</template>

<script setup>
import { mergeProps, ref } from 'vue'

const props = defineProps({ item: Object })

//  THIS IS WHERE MY PATCH REQUEST WOULD/SHOULD GO//
</script>
