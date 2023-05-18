<template>
  <div class="h-full w-full bg-white flex flex-col rounded-lg">
    <div class="flex-shrink-0">
      <img v-if="!post.video" class="h-48 w-full object-cover rounded-t-lg" :src="post.image" alt="" />
      <div v-else class="h-48">
        <iframe v-if="isShowVideo" class="w-full h-full z-[99999]" :src="post.video" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
        <div v-else class="h-48 relative">
          <img class="h-full w-full object-cover rounded-t-lg" :src="post.image" alt="" />
          <img class="center cursor-pointer" src="/images/play.svg" alt=""
          @click="isShowVideo = true">
        </div>
      </div>
    </div>
    <div class="p-6 h-full flex flex-col justify-between">
      <div class="flex flex-col gap-4">
        <p v-if="post.category" class="text-sm font-medium uppercase text-[#0048B7] cursor-pointer">
          {{ post.category }}
        </p>
        <p class="block max-h-[120px] overflow-hidden text-lg font-semibold">
          {{ post.description }}
        </p>
      </div>
      <div class="flex justify-between text-[#6B7280] text-sm">
        <p>
          {{post.time}}
        </p>
        <p>
          {{post.date}}
        </p>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: 'PrimaryCard',
  props: {
    post: {
      type: Object
    }
  },
  data() {
    return {
      isShowVideo: false
    }
  }
}
</script>
