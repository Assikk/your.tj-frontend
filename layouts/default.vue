<template>
  <section class="relative bg-[#F9F9F9]">
    <BurgerMenu class="block lg:hidden"/>
    <!-- Component SVG Icons -->
    <Icons/>
    <Banner class="hidden lg:block" :banner="banner"/>
      <Header/>
      <div class="main__container">
          <Nuxt class="pt-8 sm:pt-[60px] pb-[100px] sm:pb-[156px]"/>
      </div>
      <Footer/>
      <transition name="home">
        <Alert v-if="alert.isShow"/>
      </transition>
  </section>
</template>
<script>
import {mapState} from 'vuex'
import Banner from '@/components/banner.vue'
import Header from '~/components/header/index.vue'
import Footer from '~/components/footer/index.vue'
import Icons from '@/components/icons.vue'
import BurgerMenu from '@/components/burgerMenu.vue'
import Alert from '@/components/alert.vue'
export default {
  components: {
    Banner,
    Header,
    Footer,
    Icons,
    BurgerMenu,
    Alert
  },
  computed: {
    ...mapState({
      alert: state => state.alert
    })
  },
  data() {
    return {
      banner: {
        title: 'ADVERTISEMENT',
        image: '/images/banner.webp'
      }
    }
  }
}
</script>
