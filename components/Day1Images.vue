<script setup lang="ts">
defineProps({
  clicks: {
    default: 0,
  },
  page: {
    default: 3,
  },
})
</script>

<template>
  <div class="images">
    <img src="/images/IMG_7990.jpg" v-if="clicks === 0 && page === 3" />
    <img src="/images/IMG_7901.jpg" v-if="clicks === 1" />
    <img src="/images/IMG_7902.jpg" v-if="clicks === 2" />
    <img src="/images/IMG_7898.jpg" v-if="clicks === 3" />
    <img src="/images/IMG_7893.jpg" v-if="clicks === 4" />
    <img src="/images/IMG_7891.jpg" v-if="clicks === 5" />
    <img src="/images/IMG_7989.jpg" v-if="clicks === 6" />
    <img src="/images/IMG_7987.jpg" v-if="clicks === 7" />
  </div>
</template>

<style lang="scss" scoped>
.images {
  height: 100%;

  img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }
}
</style>