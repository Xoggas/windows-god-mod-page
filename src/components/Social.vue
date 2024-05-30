<script setup>
const props = defineProps([
  'icon',
  'link'
]);
</script>

<template>
  <a :href="link"
    target="_blank">
    <img class="icon"
      :src="icon">
  </a>
</template>

<style scoped>
a {
  width: 2.25em;
  opacity: 50%;
  transition: opacity 100ms;
}

a:hover {
  opacity: 75%;
}

img {
  width: 100%;
  height: 100%;
}
</style>