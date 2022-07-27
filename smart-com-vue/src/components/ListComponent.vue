<template>
  <ul class="list-group">
    <li v-for="item in listItems" class="list-group-item" :key="item.id">{{ item.text }}</li>
  </ul>
</template>

<script setup lang="ts">
  import {ListItem} from "@/class/ListItem";

  defineProps<{
    listItems: Array<ListItem>
  }>()
</script>

<style scoped>

</style>