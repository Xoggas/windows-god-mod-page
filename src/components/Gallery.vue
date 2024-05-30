<script setup>

import { ref, computed } from 'vue';

import ArrowIcon from "@/components/icons/ArrowIcon.vue";

const props = defineProps([
  'paths'
]);

const selectedSpriteIndex = ref(0);

const selectedSpritePath = computed(() => {
  return props.paths[selectedSpriteIndex.value];
});

function nextSprite() {
  selectedSpriteIndex.value++;

  if (selectedSpriteIndex.value >= props.paths.length) {
    selectedSpriteIndex.value = 0;
  }
}

function previousSprite() {
  selectedSpriteIndex.value--;

  if (selectedSpriteIndex.value < 0) {
    selectedSpriteIndex.value = props.paths.length - 1;
  }
}

function setSpriteByIndex(index) {
  selectedSpriteIndex.value = index;
}

</script>

<template>
  <div class="gallery">
    <div class="carousel">
      <button @click="previousSprite" class="arrow left-arrow">
        <ArrowIcon direction="left" />
      </button>
      <img :src="selectedSpritePath" class="sprite">
      <button @click="nextSprite" class="arrow right-arrow">
        <ArrowIcon direction="right" />
      </button>
    </div>
    <div class="index-dots">
      <div v-for="n in paths.length" class="index-dot-click-zone" @click="setSpriteByIndex(n - 1)">
        <div class="index-dot-fill" :selected="selectedSpriteIndex == n - 1"></div>
      </div>
    </div>
  </div>

</template>

<style scoped>
.gallery {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 100%;
}

.carousel {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
  position: relative;
  width: 100%;
}

.arrow {
  font-size: 3em;
  cursor: pointer;
  position: absolute;
}

.left-arrow {
  left: 0;
}

.right-arrow {
  right: 0;
}

.arrow span {
  font-size: inherit;
}

.arrow:hover {
  opacity: 80%;
}

.arrow:active {
  opacity: 50%;
}

.sprite {
  object-fit: contain;
  height: 5%;
}

.index-dots {
  display: flex;
  justify-content: center;
  gap: 0.5em;
  height: 12px;
  width: 100%;
}

.index-dot-click-zone {
  cursor: pointer;
  width: 100%;
  height: 100%;
  flex: 1;
  display: flex;
  align-items: center;
  transition: opacity 150ms;
}

.index-dot-click-zone:hover {
  opacity: 80%;
}

.index-dot-fill {
  width: 100%;
  height: 25%;
  background-color: rgba(255, 255, 255, 10%);
  transition: background-color 300ms;
}


.index-dot-fill[selected=true] {
  background-color: rgba(255, 255, 255, 50%);
}
</style>