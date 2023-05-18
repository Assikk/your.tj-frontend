<template>
  <div class="h-full w-full bg-white !flex flex-col rounded-lg">
    <div class="flex-shrink-0">
      <img class="h-48 w-full object-cover rounded-t-lg" src="/images/banner.webp" alt="" />
    </div>
    <div class="py-6 h-full flex flex-col justify-between">
      <div class="pb-[15px] border-b-[1px] border-dashed border-[#D7DADF]">
        <div class="px-6">
          <p class="text-[#575F6C] font-medium text-sm">
            18:00 - 12 ноября 2021, Пятница
          </p>
          <h2 class="pt-3 font-bold">
            Фото и видео выставка синематик проекта «GRAIN»
          </h2>
        </div>
      </div>
      <div class="flex flex-col gap-[6px] text-[#575F6C] text-sm px-6">
       <p>
        Бесплатно
       </p>
       <p>
        Душанбе, Отель Серена
       </p>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: 'PosterCard',
}
</script>
