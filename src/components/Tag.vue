<script setup>

const props = defineProps({
  color: { type: String, default: 'primary' },
})

</script>

<template>
  <div :class="['tag', { [`tag--${color}`]: true }]">
    <slot />
  </div>
</template>
