<script setup lang="ts">
defineProps<{ 
  list: Ref<LiveRoomItem[]>
}>()

</script>

<template>

  <!-- <List @load="load" @refresh="refresh" :immediate="true" h-full v-if="site.search.list.value.length"> -->
  <div v-if="list.value.length > 0" grid gap-4 p-2 justify-evenly  cursor-pointer select-none
    grid-cols-2 sm:grid-cols-3 md:grid-cols-4 lg:grid-cols-5 xl:grid-cols-6 class="2xl:grid-cols-7 3xl:grid"
    >
    <!-- style="grid-template-columns: repeat(auto-fill, 8rem);" -->

    <router-link :to="`/play/${room.siteId}/${room.roomId}`" v-for="room in list.value" :key="room.roomId" shadow rounded-2
      b-2px  b-solid b-transparent hover:b-amber overflow-hidden>
      <div pos-relative text-3 text-rose-4 rounded-t-2 w-full aspect-video>
        <img block v-lazy="room.cover" h-full  rounded-2 select-none>
        <div pos-absolute bottom-0 right-0 px-2 py-1 rounded-tl-2 bg-dark-6> {{ room.category }} </div>
        <div line-height-none pos-absolute top-0 right-0 px-1 py-1 rounded-tr-1 rounded-bl-2 bg-dark-6>
          <div class="i-mdi-fire"></div>
          <span>{{ room.online }}</span>
        </div>
        <div w-3 h-3 rounded-3 pos-absolute top-1 left-1 :class="[room.status ? 'bg-green' : 'bg-red']"></div>
      </div>
      <div px-2 text-truncate leading-normal> {{ room.title }}</div>
      <div px-2 text-truncate leading-normal pb-2> {{ room.nickname }} </div>

    </router-link>
  </div>

</template>

<style>


</style>