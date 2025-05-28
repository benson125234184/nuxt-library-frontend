<template>
  <div class="slider">
    <img :src="images[current]" alt="slide image" />
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const images = [
  'https://via.placeholder.com/1000x300?text=Slide+1',
  'https://via.placeholder.com/1000x300?text=Slide+2',
  'https://via.placeholder.com/1000x300?text=Slide+3',
]
const current = ref(0)

onMounted(() => {
  setInterval(() => {
    current.value = (current.value + 1) % images.length
  }, 3000)
})
</script>

<style scoped>
.slider img {
  width: 100%;
  height: auto;
}
</style>
