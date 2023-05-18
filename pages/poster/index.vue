<template>
  <div class="flex flex-col gap-6">
    <Carousel
    title="Афиша"/>
    <Banner :banner="banner"/>
    <div>
      <div class="flex items-center justify-between mb-6">
          <p class="font-bold text-lg sm:text-[26px]">
            Новости
          </p>
        <div class="hidden sm:flex gap-4 items-center">
          <svg class="cursor-pointer rotate-180" fill="black" width="32" height="32"
          @click="$refs.news.prev()">
            <use xlink:href="#arrow"/>
          </svg>
          <svg class="cursor-pointer" fill="black" width="32" height="32"
          @click="$refs.news.next()">
            <use xlink:href="#arrow"/>
          </svg>
        </div>
      </div>
      <div>
        <VueSlickCarousel v-bind="settings" ref="news">
          <div v-for="i in 12" :key="i">
            <Card :post="news[9]"/>
          </div>
        </VueSlickCarousel>
      </div>
    </div>
    <Banner :banner="banner"/>
    <div>
      <div class="flex items-center justify-between mb-6">
          <p class="font-bold text-lg sm:text-[26px]">
            Истории
          </p>
        <div class="hidden sm:flex gap-4 items-center">
          <svg class="cursor-pointer rotate-180" fill="black" width="32" height="32"
          @click="$refs.history.prev()">
            <use xlink:href="#arrow"/>
          </svg>
          <svg class="cursor-pointer" fill="black" width="32" height="32"
          @click="$refs.history.next()">
            <use xlink:href="#arrow"/>
          </svg>
        </div>
      </div>
      <div>
        <VueSlickCarousel v-bind="settings" ref="history">
          <div v-for="i in 12" :key="i">
            <Card :post="news[9]"/>
          </div>
        </VueSlickCarousel>
      </div>
    </div>
    <Banner :banner="banner"/>
    <div>
      <div class="flex items-center justify-between mb-6">
          <p class="font-bold text-lg sm:text-[26px]">
            Подкасты
          </p>
        <div class="hidden sm:flex gap-4 items-center">
          <svg class="cursor-pointer rotate-180" fill="black" width="32" height="32"
          @click="$refs.history.prev()">
            <use xlink:href="#arrow"/>
          </svg>
          <svg class="cursor-pointer" fill="black" width="32" height="32"
          @click="$refs.history.next()">
            <use xlink:href="#arrow"/>
          </svg>
        </div>
      </div>
      <div>
        <VueSlickCarousel v-bind="settings" ref="history">
          <div v-for="i in 12" :key="i">
            <Card :post="news[2]"/>
          </div>
        </VueSlickCarousel>
      </div>
    </div>
  </div>
</template>
<script>
import {mapState} from 'vuex'
import VueSlickCarousel from 'vue-slick-carousel'
import 'vue-slick-carousel/dist/vue-slick-carousel.css'
// optional style for arrows & dots
import 'vue-slick-carousel/dist/vue-slick-carousel-theme.css'
import Carousel from '@/components/carousel.vue'
import Card from '@/components/card/history.vue'
export default {
  name: 'PosterPage',
  components: {
    Carousel,
    Card,
    VueSlickCarousel,
  },
  computed: {
    ...mapState({
      news: state => state.news
    })
  },
  data() {
    return {
      banner: {
        title: 'ADVERTISEMENT',
        image: '/images/news/10.webp'
      },
      settings: {
        "dots": false,
        "arrows": true,
        "infinite": false,
        "speed": 500,
        "slidesToShow": 3,
        "slidesToScroll": 3,
        "responsive": [
          {
            "breakpoint": 768,
            "settings": {
              "slidesToShow": 2,
              "slidesToScroll": 2,
            }
          },
          {
            "breakpoint": 640,
            "settings": {
              "slidesToShow": 1,
              "slidesToScroll": 1,
            }
          },
        ]
      }
    }
  }
}
</script>
<style scoped>
@media screen and (min-width: 640px) {
  ::v-deep .slick-slide {
    padding: 0 12px;
  }
}
</style>
