<template>
  <div class="winding-path">
    <div class="path">
      <div
        v-for="(carousel, index) in carousels"
        :key="index"
        class="pointer"
        :style="{
          left: `${carousel.position.x}px`,
          top: `${carousel.position.y}px`,
        }"
        @click="toggleCarousel(index)"
      >
        <div class="pointer-icon">{{ index + 1 }}</div>
      </div>
    </div>
    <PhotoCarousel
      v-for="(carousel, index) in carousels"
      v-if="carousel.isExpanded"
      :key="index"
      :photos="carousel.photos"
    />
  </div>
</template>

<script>
import PhotoCarousel from "./PhotoCarousel.vue";

export default {
  components: {
    PhotoCarousel,
  },
  data() {
    return {
      carousels: [
        { position: { x: 50, y: 100 }, isExpanded: false, photos: [] },
        { position: { x: 150, y: 200 }, isExpanded: false, photos: [] },
        { position: { x: 250, y: 150 }, isExpanded: false, photos: [] },
        // Add more carousels as needed
      ],
    };
  },
  methods: {
    toggleCarousel(index) {
      this.carousels[index].isExpanded = !this.carousels[index].isExpanded;
      if (this.carousels[index].photos.length === 0) {
        this.fetchPhotos(index); // Fetch photos if not already fetched
      }
    },
    fetchPhotos(index) {
      // Fetch photos from your API and assign to carousels[index].photos
      // Example:
      // axios.get('YOUR_API_ENDPOINT').then(response => {
      //   this.carousels[index].photos = response.data;
      // });
    },
  },
};
</script>

<style scoped>
.winding-path {
  position: relative;
  height: 400px; /* Adjust as needed */
  overflow: hidden;
}
.path {
  position: absolute;
  width: 100%;
  height: 100%;
  background: url("path-to-your-winding-path-image.png") no-repeat center center;
  background-size: cover;
}
.pointer {
  position: absolute;
  cursor: pointer;
}
.pointer-icon {
  background-color: #fff;
  border-radius: 50%;
  padding: 10px;
  text-align: center;
  box-shadow: 0 0 5px rgba(0, 0, 0, 0.5);
}
</style>
