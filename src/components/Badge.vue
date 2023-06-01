<script setup>
import { computed } from 'vue';

const props = defineProps({
  count: { type: Number, default: 0 },
  dark: { type: Boolean, default: false }
})

const color = computed(() => {
  switch (props.count) {
    case 4:
      return 'danger';

    case 3:
      return 'warning';

    case 2:
      return 'info';

    case 1:
      return 'success';

    default:
      return 'primary';
  }
})

</script>

<template>
  <div :class="['badge', { [`badge--${color}`]: true }, { [`badge--dark`]: true }]">
    {{ count }}
  </div>
</template>
