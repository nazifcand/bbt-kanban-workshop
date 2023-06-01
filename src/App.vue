<script setup>
import columns from '../data.json';
import Kanban from './components/Kanban.vue'
import Button from './components/Button.vue'

</script>

<template>
  <div class="container">
    <Button
      color="success"
      large
    >Yeni Görev</Button>
  </div>
  <div class="container">
    <Kanban :columns="columns" />
  </div>
</template>
