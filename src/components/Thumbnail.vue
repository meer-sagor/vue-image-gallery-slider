<!-- eslint-disable vue/multi-word-component-names -->
<script setup>
import { Thumbs } from "swiper";
import { Swiper, SwiperSlide } from "swiper/vue";

const emits = defineEmits(["thumbs", "update:currentSlide"]);

const onSwiper = (swiper) => {
  emits("thumbs", swiper);
};
</script>

<template>
  <Swiper
    @swiper="onSwiper"
    :slides-per-view="10"
    :space-between="50"
    :modules="[Thumbs]"
    watch-slides-progress
  >
    <SwiperSlide
      v-for="n in 20"
      :key="n"
      @click.stop="$emit('update:currentSlide', Number(n) - 1)"
    >
      <img
        :src="'https://picsum.photos/id/' + n + '/640/480'"
        style="height: 100px"
      />
    </SwiperSlide>
  </Swiper>
</template>
