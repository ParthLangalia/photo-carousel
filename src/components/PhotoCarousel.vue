<template>
  <div class="carousel-container" :class="{ minimized: isMinimized }">
    <button @click="toggleMinimize">
      {{ isMinimized ? "Expand" : "Minimize" }}
    </button>
    <div class="carousel" v-if="!isMinimized">
      <div
        class="carousel-inner"
        :style="{ transform: `translateX(-${currentIndex * 100}%)` }"
      >
        <div
          class="carousel-item"
          v-for="(photo, index) in photos"
          :key="index"
        >
          <img :src="photo.url" :alt="photo.title" />
        </div>
      </div>
      <button @click="prevSlide">Prev</button>
      <button @click="nextSlide">Next</button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    photos: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {
      currentIndex: 0,
      isMinimized: false,
    };
  },
  methods: {
    nextSlide() {
      this.currentIndex = (this.currentIndex + 1) % this.photos.length;
    },
    prevSlide() {
      this.currentIndex =
        (this.currentIndex - 1 + this.photos.length) % this.photos.length;
    },
    toggleMinimize() {
      this.isMinimized = !this.isMinimized;
    },
  },
};
</script>

<style scoped>
/* Add your styles here */
</style>
