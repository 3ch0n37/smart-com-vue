<template>
  <ul class="list-group p-3"
      @drop="onDrop($event)"
      @dragover.prevent
      @dragenter.prevent
  >
    <li v-for="item in listItems"
        class="list-group-item"
        :key="item.id"
        draggable="true"
        @dragstart="startDrag($event, item)"
    >{{ item.text }}</li>
  </ul>
  <br>
  <pre>{{listItems}}</pre>
</template>

<script setup lang="ts">
  import {ListItem} from "@/class/ListItem";

  defineProps<{
    listItems: Array<ListItem>
  }>()

  const emit = defineEmits(['startDrag', 'onDrop'])

  function startDrag(evt: DragEvent, item: ListItem) {
    emit('startDrag', evt, item)
  }

  function onDrop(evt: DragEvent) {
    emit('onDrop', evt)
  }
</script>

<style scoped>
  ul {
    background-color: #eee;
  }
</style>