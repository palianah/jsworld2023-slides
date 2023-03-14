<script setup lang="ts">
import { onUnmounted, ref, watch } from 'vue';
import { watchOnce } from "@vueuse/core";

const props = defineProps({
  clicks: {
    default: 0,
  },
  page: {
    default: 3,
  },
})

const toggleShow = ref(false);

watchOnce(() => props.clicks, () => {
  setTimeout(() => {
    toggleShow.value = true;
  }, 100);
});

watch(() => props.clicks, (clickCount) => {
  if (clickCount === 0) {
    toggleShow.value = false;
  }
});

onUnmounted(() => {
  toggleShow.value = true;
});
</script>

<template>
  <div class="images" v-if="toggleShow">
    <img src="/images/IMG_7990.jpg" v-if="clicks === 0 && page === 3" />
    <img src="/images/js-world-1200x800.jpeg" v-if="clicks === 1" />
    <img src="/images/IMG_7901.jpg" v-if="clicks === 2" />
    <img src="/images/IMG_7898.jpg" v-if="clicks === 3" />
    <img src="/images/IMG_7989.jpg" v-if="clicks === 4" />
    <img src="/images/IMG_7987.jpg" v-if="clicks === 5" />
    <img src="/images/IMG_7893.jpg" v-if="clicks === 6" />
    <img src="/images/IMG_7891.jpg" v-if="clicks === 7" />
    <img src="/images/speakers.png" v-if="clicks === 8" />
    <img src="/images/IMG_7890.jpg" v-if="clicks === 9" />
    <img src="/images/van-gogh-museum.jpeg" v-if="clicks === 10" />
  </div>
</template>

<style lang="scss" scoped>
.images {
  height: 100%;

  img {
    width: 100%;
    height: 100%;
    object-fit: contain;
  }
}
</style>