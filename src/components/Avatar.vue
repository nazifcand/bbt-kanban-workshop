<script setup>
import { computed } from 'vue';

const props = defineProps({
  image: { type: String, default: null },
  text: { type: String, required: true },
  circle: { type: Boolean, default: false }
})

const shortText = computed(() => props.text.split(' ').map(item => item[0]).join(''))
</script>

<template>
  <img
    v-if="image"
    :src="image"
    :class="['user-avatar', { 'user-avatar-circle': circle }]"
  >
  <div
    v-else
    class="user-avatar-text"
  >
    {{ shortText }}
  </div>
</template>
