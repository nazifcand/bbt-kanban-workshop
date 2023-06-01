<script setup>

import KanbanColumn from './KanbanColumn.vue';

const props = defineProps({
  columns: { type: Array, defualt: [] }
})


</script>

<template>
  <!-- .kanban start -->
  <div class="kanban">

    <KanbanColumn
      v-for="(item, index) in columns"
      :key="index"
      :title="item.title"
      :tasks="item.tasks"
    />

  </div>
  <!-- .kanban -->
</template>
