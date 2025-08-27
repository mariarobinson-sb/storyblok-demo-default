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
      :space-between="10"
      :navigation="true"
      :autoplay="true"
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
