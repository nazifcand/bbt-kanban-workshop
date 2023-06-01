<script setup>

import Tag from './Tag.vue';
import Avatar from './Avatar.vue';
import Button from './Button.vue';

const props = defineProps({
  id: { type: Number, required: true },
  summary: { type: String, default: '' },
  created: { type: String, default: '' },
  tags: { type: Array, default: [] },
  user: { type: Object, required: true },
})

const handleClick = id => alert(`silinecek task ID => ${id}`)
</script>

<template>
  <!-- .kanban-task start -->
  <div class="kanban-task">
    <!-- .task-header start -->
    <div class="task-header">

      <!-- .tag-lis start -->
      <div class="tag-list">
        <Tag
          v-for="(tag, index) in tags"
          :key="index"
          :color="tag.color"
        >{{ tag.text }}</Tag>
      </div>
      <!-- .tag-list  -->

      <!-- .task-dropdown start -->
      <div class="task-dropdown">
        <i class="fa-solid fa-ellipsis"></i>
      </div>
      <!-- .task-dropdown  -->

    </div>
    <!-- .task-header  -->

    <!-- .task-details start -->
    <div class="task-details">
      <!-- .task-detail start -->
      <div class="task-detail">
        <span>Task ID</span>
        <strong>{{ id }}</strong>
      </div>
      <!-- .task-detail  -->

      <!-- .task-detail start -->
      <div class="task-detail">
        <span>Yaratılış Tarihi</span>
        <strong>{{ created }}</strong>
      </div>
      <!-- .task-detail  -->
    </div>
    <!-- .task-details  -->

    <!-- .task-summary start -->
    <div class="task-summary">
      <p>{{ summary }}</p>
    </div>
    <!-- .task-summary  -->

    <!-- .task-user start -->
    <div class="task-user">
      <Avatar
        :text="user.name"
        :image="user.image"
        :circle="user.name.split(' ').length == 2"
      />
      <strong>{{ user.name }}</strong>
    </div>
    <!-- .task-user  -->

    <Button
      color="danger"
      @click="handleClick(id)"
    >SIL</Button>

  </div>
  <!-- .kanban-task  --></template>
