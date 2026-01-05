<template>
  <div class="app-container">
    <div class="snow"></div>
    <SlideCarousel />
    <router-view />
  </div>
</template>

<script setup>
import SlideCarousel from './components/SlideCarousel.vue'
</script>

<style scoped>
.app-container {
  position: relative;
  width: 100%;
  min-height: 100vh;
}
</style>

