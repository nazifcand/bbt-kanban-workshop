<script setup>
import KanbanTask from './KanbanTask.vue'
import Badge from './Badge.vue';

const props = defineProps({
  title: { type: String, default: '' },
  tasks: { type: Array, default: [] },
})

</script>

<template>
  <!-- .kanban-column start -->
  <div class="kanban-column">
    <!-- .column-header start -->
    <div class="column-header">
      <!-- .column-title start -->
      <div class="column-title">
        {{ title }}
      </div>
      <!-- .column-title -->

      <Badge :count="tasks.length" />
    </div>
    <!-- .column-header -->


    <KanbanTask
      v-for="(task, index) in tasks"
      :key="index"
      :id="task.id"
      :summary="task.summary"
      :created="task.createdAt"
      :tags="task.tags"
      :user="task.user"
    />

  </div>
  <!-- .kanban-column -->
</template>
