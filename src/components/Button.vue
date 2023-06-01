<script setup>
const props = defineProps({
  color: { type: String, default: 'primary' },
  large: { type: Boolean, default: false }
})

</script>

<template>
  <button
    type="button"
    :class="['button', { [`button--${color}`]: true }, { [`button--large`]: large }]"
  >
    <slot />
  </button>
</template>
