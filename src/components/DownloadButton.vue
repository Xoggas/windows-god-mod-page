<script setup>

import DownloadIcon from "@/components/icons/DownloadIcon.vue";

defineProps([
  'href'
]);

</script>

<template>
  <a class="download-button" :href="href" download>
    <slot />
    <DownloadIcon />
  </a>
</template>

<style scoped>
.download-button {
  display: flex;
  padding: 1em 2em;
  border: 1px solid var(--border-color-2);
  align-items: center;
  justify-content: space-between;
  transition: background-color, opacity 150ms;
}

.download-button:hover {
  background-color: var(--block-color-2);
}

.download-button:active {
  opacity: 50%;
}
</style>