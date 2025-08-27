<script setup>
import { Swiper, SwiperSlide } from 'swiper/vue'
import { Autoplay, Navigation } from 'swiper/modules'
import 'swiper/css'
import 'swiper/css/navigation'
const props = defineProps({ blok: Object })

const modules = [Autoplay, Navigation]
</script>

<style scoped>
.swiper {
  --swiper-theme-color: var(--medium);
}
</style>

<template>
  <section
    v-editable="blok"
    class="page-section banner-reference-section bg-white"
  >
    <swiper
      :slides-per-view="1"
      :navigation="true"
      :autoplay="{
        delay: 6000, // 6 seconds
        disableOnInteraction: false, // Optional: keeps autoplay running after user interaction
      }"
      :speed="1000"
      :auto-height="true"
      :modules="modules"
      :loop="true"
      class="swiper"
    >
      <swiper-slide v-for="banner in blok.banners" :key="banner.uuid">
        <Banner
          v-if="banner.content"
          :blok="banner.content"
          :referenced="true"
        />
      </swiper-slide>
    </swiper>
  </section>
</template>
