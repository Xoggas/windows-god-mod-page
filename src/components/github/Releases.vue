<script setup>

import { onMounted, ref, computed } from 'vue';

import Release from './Release.vue';
import ErrorIcon from '@/components/icons/ErrorIcon.vue';

const PROFILE_NAME = import.meta.env.VITE_GITHUB_PROFILE_NAME;
const REPOSITORY_NAME = import.meta.env.VITE_GITHUB_REPOSITORY_NAME;

const isLoading = ref(false);
const hasFailed = ref(false);
const releases = ref([]);
const isEmpty = computed(() => releases.value.length == 0 || releases == null);

onMounted(async () => {
  try {
    releases.value = await loadReleases();
  }
  catch {
    hasFailed = true;
  }
});

async function loadReleases() {
  const apiUrl = `https://api.github.com/repos/${PROFILE_NAME}/${REPOSITORY_NAME}/releases`;

  isLoading.value = true;

  const response = await fetch(apiUrl);

  isLoading.value = false;

  if (response.ok == false) {
    throw new Error("Couldn't load the releases");
  }

  return await response.json();
}

</script>

<template>
  <div v-if="isLoading" class="preloader"></div>
  <div v-else-if="hasFailed" class="error-banner">
    <ErrorIcon />
    <p>Couldn't load the releases!</p>
  </div>
  <div v-else-if="isEmpty" class="no-releases-banner">
    <p>There are no releases yet!</p>
  </div>
  <div v-else class="releases">
    <Release v-for="(release, index) in releases" :name="release.name" :isLatest="index == 0"
      :isPrerelease="release.prerelease" :assets="release.assets" />
  </div>
</template>

<style scoped>
.preloader {
  width: 100%;
  height: 12em;
  border-radius: 2px;
  background-color: var(--block-color-1);
  animation: shimmer 1s ease-in-out infinite alternate;
}

@keyframes shimmer {
  0% {
    background-color: var(--block-color-1);
  }

  100% {
    background-color: var(--block-color-2);
  }
}

.error-banner {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 12em;
  gap: 1em;
  border: 1px solid var(--border-color-2);
}

.error-banner span {
  color: var(--border-color-1);
}

.error-banner p {
  color: var(--border-color-1);
}

.no-releases-banner {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 12em;
  border: 1px solid var(--border-color-2);
}

.no-releases-banner p {
  color: var(--border-color-1);
}

.releases {
  display: flex;
  flex-direction: column;
  gap: 1.5em;
  height: max-content;
  margin-bottom: 2em;
}
</style>