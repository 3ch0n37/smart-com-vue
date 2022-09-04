<script setup lang="ts">
    import type { ListItem } from '@/class/ListItem';
    import { reactive, ref } from 'vue';
    import draggable from 'vuedraggable'

    defineProps<{
        listItems: Array<ListItem>
    }>()
    
    const items = reactive([
            {text: "AAA", id: 1},
            {text: "BBB", id: 2}
        ])
    const drag = ref(false);
</script>
    
<template>
    <draggable 
    class="list-group p-3"
    v-model="listItems" 
    group="items" 
    @start="drag = true"
     @end="drag = false" 
     item-key="id">
        <template #item="{ element }">
            <div class="list-group-item">{{element.text}}</div>
        </template>
    </draggable>
    <pre>{{listItems}}</pre>
</template>
    
<style scoped>
    .list-group {
    background-color: #eee;
  }
</style>