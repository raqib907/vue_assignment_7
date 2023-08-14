

<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue';
import PieChart from "./components/PieChart.vue";

const slides = [
  'image1.jpg',
  'image2.jpg',
  'image3.jpg',
  // Add more image URLs here
];

const currentSlide = ref(0);

const prevSlide = () => {
  currentSlide.value = (currentSlide.value - 1 + slides.length) % slides.length;
};

const nextSlide = () => {
  currentSlide.value = (currentSlide.value + 1) % slides.length;
};

const interval = setInterval(nextSlide, 5000); // Auto-advance every 5 seconds

onMounted(() => {
  // Initialization logic here
});

onBeforeUnmount(() => {
  clearInterval(interval);
});
</script>


<template>
  <div class="carousel">
    <button @click="prevSlide">Previous</button>
    <div class="slide-container">
      <transition name="fade" mode="out-in">
        <img :key="currentSlide" :src="slides[currentSlide]" alt="Carousel Slide" />
      </transition>
    </div>
    <button @click="nextSlide">Next</button>
  </div>

  <PieChart></PieChart>
</template>



<style>
/* Add your styles for the carousel here */
</style>
