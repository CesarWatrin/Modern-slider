<script lang="ts" setup>
import { ref } from "vue";
import Slide from "@/components/Slide.vue";

const images = ref<Array<string>>([
  "image_1.jpg",
  "image_2.jpg",
  "image_3.jpg",
  "image_4.jpg",
  "image_5.jpg",
  "image_6.jpg",
  "image_7.jpg",
]);

const next = () => {
  return true;
};

const back = () => {
  return true;
};
</script>

<template>
  <div class="py-8 px-4 bg-white overflow-hidden">
    <div class="flex">
      <Slide v-for="(image, idx) in images" :key="idx" :image="image" />
    </div>
    <div class="mt-8 mx-4 flex">
      <div
        class="py-4 px-8 mr-4 bg-amber-500 rounded-lg cursor-pointer"
        @click="back"
      >
        Back
      </div>
      <div
        class="py-4 px-8 mr-4 bg-amber-500 rounded-lg cursor-pointer"
        @click="next"
      >
        Next
      </div>
    </div>
  </div>
</template>
