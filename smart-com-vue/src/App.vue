<script setup lang="ts">
import 'bootstrap'
import 'bootstrap/dist/css/bootstrap.css'
import ListComponent from './components/ListComponent.vue'
import {ListItem} from "@/class/ListItem";

const list1: Array<ListItem> = [
  {text: 'AAA', id: 0},
  {text: 'CCC', id: 2}
]

const list2: Array<ListItem> = [
  {text: 'BBB', id: 1},
  {text: 'DDD', id: 3}
]
</script>

<template>
  <main>
    <div class="container">
      <h2>Smart Com challenge</h2>
      <p>Lists with drag-drop functionality. Made using Vue, Typescript, Bootstrap and native D&D APIs</p>
      <div class="row">
        <div class="col-6">
          <ListComponent :list-items="list1"/>
        </div>
        <div class="col-6">
          <ListComponent :list-items="list2"/>
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped>

</style>
