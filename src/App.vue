<script setup>
import PhotoCarousel from "./components/PhotoCarousel.vue";
import WindingPath from "./components/WindingPath.vue";
</script>

<template>
  <div id="app">
    <WindingPath />
    <PhotoCarousel />
  </div>
</template>

<script>
import WindingPath from "./components/WindingPath.vue";
import PhotoCarousel from "./components/PhotoCarousel.vue";

export default {
  components: {
    WindingPath,
    PhotoCarousel,
  },
};
</script>
