<!-- eslint-disable vue/multi-word-component-names -->
<script setup>
import { Navigation, Pagination, A11y, Lazy } from "swiper";
import { Swiper, SwiperSlide } from "swiper/vue";
// Import Swiper styles
import "swiper/css";
import "swiper/css/bundle";
</script>

<template>
  <Swiper
    :slides-per-view="1"
    :space-between="50"
    :modules="[Navigation, Pagination, A11y, Lazy]"
    navigation
    :pagination="{ clickable: true, dynamicBullets: true }"
    grabCursor
    :preloadImages="false"
    lazy
  >
    <SwiperSlide
      v-for="n in 1000"
      :key="n"
      :virtualIndex="n"
      class="customSlider"
    >
      <img
        :data-src="'https://picsum.photos/1024/600?random=' + n"
        alt=""
        class="swiper-lazy"
      />
      <div class="swiper-lazy-preloader"></div>
    </SwiperSlide>
  </Swiper>
</template>

<style scoped>
.customSlider {
  display: grid;
  place-items: center;
  height: 100vh;
}
</style>
