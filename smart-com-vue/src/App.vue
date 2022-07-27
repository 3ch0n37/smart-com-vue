<script setup lang="ts">
import 'bootstrap'
import 'bootstrap/dist/css/bootstrap.css'
import ListComponent from './components/ListComponent.vue'
import type {ListItem} from "@/class/ListItem";
import {computed, ref} from "vue";
import type {Ref} from "vue";

const listContents: Ref<Array<ListItem>> = ref([
  {text: 'AAA', id: 0, listId: 1},
  {text: 'CCC', id: 2, listId: 1},
  {text: 'BBB', id: 1, listId: 2},
  {text: 'DDD', id: 3, listId: 2}
])

const list1: Ref<Array<ListItem>> = computed(() => {
  return listContents.value.filter((li) => li.listId == 1)
})

const list2: Ref<Array<ListItem>> = computed(() => {
  return listContents.value.filter((li) => li.listId == 2)
})

function startDrag(evt: DragEvent, item: ListItem) {
  if (evt.dataTransfer && item.id) {
    evt.dataTransfer.dropEffect = 'move'
    evt.dataTransfer.effectAllowed = 'move'
    evt.dataTransfer.setData('itemId', item.id.toString())
  }
}

function onDrop(evt: DragEvent, list: number) {
  if (evt.dataTransfer) {
    const itemId = parseInt(evt.dataTransfer.getData('itemId'))
    const item = listContents.value.find((item) => item.id == itemId)
    if (item) {
      item.listId = list
    }
  }
}
</script>

<template>
  <main>
    <div class="container">
      <h2>Smart Com challenge</h2>
      <p>Lists with drag-drop functionality. Made using Vue, Typescript, Bootstrap and native D&D APIs</p>
      <div class="row">
        <div class="col-6">
          <ListComponent
              :list-items="list1"
              @startDrag="(evt, item) => {startDrag(evt, item)}"
              @onDrop="(evt) => {onDrop(evt, 1)}"
          />
        </div>
        <div class="col-6">
          <ListComponent
              :list-items="list2"
              @startDrag="(evt, item) => {startDrag(evt, item)}"
              @onDrop="(evt) => {onDrop(evt, 2)}"
          />
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped>

</style>
