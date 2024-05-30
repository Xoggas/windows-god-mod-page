<script setup>

defineProps([
  'isExpanded'
]);

</script>

<template>
  <span v-if="isExpanded" class="material-symbols-rounded" :class="$attrs.class">
    arrow_drop_up
  </span>
  <span v-else class="material-symbols-rounded" :class="$attrs.class">
    arrow_drop_down
  </span>
</template>

<style scoped>
.material-symbols-rounded {
  font-size: 2em;
  font-variation-settings: 'wght' 300;
}
</style>