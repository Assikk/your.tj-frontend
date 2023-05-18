<template>
  <div class="flex flex-col gap-6">
    <div class="grid gap-5 lg:max-w-none lg:grid-cols-3">
      <div v-for="post in news.slice(0,3)" :key="post.id" class="flex flex-col overflow-hidden rounded-lg shadow-lg h-[439px]">
        <PrimaryCard :post="post"/>
      </div>
    </div>
    <SecondaryCard
    :post="news[3]"/>
    <div class="h-[354px] sm:h-[475px]">
      <PhotoCard :post="news[4]"/>
    </div>
    <SecondaryCard
    :post="news[3]"/>
    <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
      <div class="h-[354px]" v-for="post in news.slice(6,8)" :key="post.id">
        <PhotoCard :post="post"/>
      </div>
    </div>
    <div class="grid gap-5 lg:max-w-none lg:grid-cols-3">
      <div v-for="post in news.slice(6,8)" :key="post.id" class="flex flex-col overflow-hidden rounded-lg h-[439px]">
        <PrimaryCard :post="post"/>
      </div>
      <MailingCard
      v-model="email"
      @subscribe="subscribe"/>
    </div>
    <Carousel
    title="Афиша"/>
    <Banner :banner="banner"/>
    <Carousel
    title="Спецпроекты"/>
    <SecondaryCard
    :post="news[3]"/>
    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6">
      <PrimaryCard :post="news[7]" class="h-[440px]"/>
      <img class="h-full w-full object-cover rounded-md h-[440px]" src="/images/news/10.webp" alt="">
      <PrimaryCard :post="news[8]" class="h-[440px]"/>
    </div>
    <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-6">
      <div class="flex flex-col h-[259px] sm:h-[296px]" v-for="num in 4" :key="num">
        <div>
          <img class="w-full h-[154px] sm:h-[171px] rounded-none sm:rounded-md" src="/images/news/1.webp" alt="">
        </div>
        <div class="pt-4 sm:pt-6 flex flex-col justify-between gap-4 h-full">
          <p class="max-h-[66px] overflow-hidden font-semibold text-sm sm:text-base">
            Как в Турсунзаде смогли сохранить одну из самых больших школ дутара в Таджикистане
          <div class="flex justify-between items-center text-sm text-[#6B7280]">
            <p>
              12:00
            </p>
            <p>
              01.01.2023
            </p>
          </div>
        </div>
      </div>
    </div>
    <Banner :banner="banner"/>
  </div>
</template>
<script>
import PrimaryCard from '@/components/card/primary.vue'
import SecondaryCard from '@/components/card/secondary.vue'
import PhotoCard from '@/components/card/photo.vue'
import MailingCard from '@/components/card/mailing.vue'
import Carousel from '@/components/carousel.vue'
import validateEmail from '@/helpers/validateEmail'
import {mapState, mapMutations} from 'vuex'
export default {
  name: 'IndexPage',
  components: {
    PrimaryCard,
    SecondaryCard,
    PhotoCard,
    MailingCard,
    Carousel
  },
  computed: {
    ...mapState({
      news: state => state.news
    })
  },
  data() {
    return {
      email: null,
      banner: {
        title: 'ADVERTISEMENT',
        image: '/images/news/10.webp'
      }
    }
  },
  methods: {
    ...mapMutations({
      change_state: 'CHANGE_STATE',
      clear_alert: 'CLEAR_ALERT'
    }),
    subscribe() {
      let payload
      if(this.email == null) {
        payload = {
          key: 'alert',
          body: {
            isShow: true,
            msg: 'Введите почту',
            type: 'error'
          }
        }
        this.change_state(payload)
        setTimeout(() => {
          this.clear_alert()
        }, 2000)
      } else if(!validateEmail(this.email)) {
        payload = {
          key: 'alert',
          body: {
            isShow: true,
            msg: 'Почта введена неккоретно',
            type: 'error'
          }
        }
        this.change_state(payload)
        setTimeout(() => {
          this.clear_alert()
        }, 2000)
      } else {
        payload = {
          key: 'alert',
          body: {
            isShow: true,
            msg: 'Вы успешно подписались на рассылку!',
            type: 'success'
          }
        }
        this.change_state(payload)
        setTimeout(() => {
          this.clear_alert()
        }, 2000)
      }
    }
  },
}
</script>
