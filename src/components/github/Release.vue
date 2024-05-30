<script setup>

import { ref } from 'vue';

import DownloadButton from '@/components/DownloadButton.vue';
import DropDownArrowIcon from '@/components/icons/DropDownArrowIcon.vue';

const props = defineProps([
  'name',
  'isLatest',
  'isPrerelease',
  'assets'
]);

const isExpanded = ref(false);

</script>

<template>
  <div class="release">
    <div @click="isExpanded = !isExpanded" :expanded="isExpanded" class="header">
      <p>{{ name }}</p>
      <div v-if="isLatest" class="tag">latest</div>
      <div v-if="isPrerelease" class="tag">pre-release</div>
      <DropDownArrowIcon class="dropdown-arrow" :isExpanded="isExpanded" />
    </div>
    <div v-show="isExpanded" class="body">
      <h2>Files</h2>
      <DownloadButton :href="asset.browser_download_url" v-for="asset in assets">
        <p>{{ asset.name }}</p>
      </DownloadButton>
    </div>
  </div>
</template>

<style scoped>
.release {
  display: flex;
  flex-direction: column;
}

.header {
  display: flex;
  padding: 1em 2em;
  border: 1px solid var(--border-color-2);
  align-items: center;
  transition: background-color, opacity 150ms;
  gap: 1.25em;
  cursor: pointer;
}

.header[expanded=true] {
  background-color: var(--block-color-1);
}

.header:hover {
  background-color: var(--block-color-2);
}

.tag {
  border: 1px solid var(--border-color-1);
  color: var(--border-color-1);
  padding: 0.35em 1em;
  border-radius: 100px;
}

.dropdown-arrow {
  margin-left: auto;
}

.body {
  display: flex;
  flex-direction: column;
  padding: 2em;
  border: 1px solid var(--border-color-2);
  border-top-width: 0;
  gap: 1em;
  font-size: 0.8em;
}
</style>