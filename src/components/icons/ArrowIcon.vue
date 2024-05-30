<script setup>

const directions = {
  left: 'left',
  right: 'right',
  up: 'up',
  down: 'down'
};

defineProps([
  'direction'
]);

</script>

<template>
  <span v-if="direction == directions.left" class="material-symbols-rounded">
    chevron_left
  </span>
  <span v-if="direction == directions.right" class="material-symbols-rounded">
    chevron_right
  </span>
</template>

<style scoped>
.material-symbols-rounded {
  font-size: 1.5em;
  font-variation-settings: 'wght' 300;
}
</style>