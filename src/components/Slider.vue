<script lang="ts" setup>
import {ref, watch} from "vue";
import Slide from "@/components/Slide.vue";
import type { ISlide } from "@/interfaces/slide.interface";

const allWidth = [];

const slides = ref<Array<ISlide>>([
  {
    image: "image_1.jpg",
    width: ["min-w-[800px]", "min-w-[150px]", "min-w-[0px] mx-0"],
  },
  {
    image: "image_2.jpg",
    width: [
      "min-w-[400px]",
      "min-w-[800px]",
      "min-w-[150px]",
      "min-w-[0px] mx-0",
    ],
  },
  {
    image: "image_3.jpg",
    width: [
      "min-w-[200px]",
      "min-w-[400px]",
      "min-w-[800px]",
      "min-w-[150px]",
      "min-w-[0px] mx-0",
    ],
  },
  {
    image: "image_4.jpg",
    width: [
      "min-w-[200px]",
      "min-w-[200px]",
      "min-w-[400px]",
      "min-w-[800px]",
      "min-w-[150px]",
      "min-w-[0px] mx-0",
    ],
  },
  {
    image: "image_5.jpg",
    width: [
      "min-w-[200px]",
      "min-w-[200px]",
      "min-w-[200px]",
      "min-w-[400px]",
      "min-w-[800px]",
      "min-w-[150px]",
      "min-w-[0px] mx-0",
    ],
  },
  {
    image: "image_6.jpg",
    width: [
      "min-w-[200px]",
      "min-w-[200px]",
      "min-w-[200px]",
      "min-w-[200px]",
      "min-w-[400px]",
      "min-w-[800px]",
      "min-w-[150px]",
      "min-w-[0px] mx-0",
    ],
  },
  {
    image: "image_7.jpg",
    width: [
      "min-w-[200px]",
      "min-w-[200px]",
      "min-w-[200px]",
      "min-w-[200px]",
      "min-w-[200px]",
      "min-w-[400px]",
      "min-w-[800px]",
      "min-w-[150px]",
      "min-w-[0px] mx-0",
    ],
  },
]);

const widthIndex = ref<number>(1);

const next = () => {
  if (widthIndex.value < slides.value.length - 1) {
    widthIndex.value++;
  }
};

const back = () => {
  if (widthIndex.value > 0) {
    widthIndex.value--;
  }
};

const dragged = ref(false);
const oldX = ref(0);
window.addEventListener("mousedown", function (e) {
  oldX.value = e.pageX;
  dragged.value = false;
});
document.addEventListener("mousemove", function () {
  dragged.value = true;
});
window.addEventListener("mouseup", function (e) {
  if (dragged.value == true && e.pageX < oldX.value) {
    next();
  } else if (dragged.value == true && e.pageX > oldX.value) {
    back();
  }
});
window.addEventListener("touchstart", function (e) {
  oldX.value = e.changedTouches[0].pageX;
  dragged.value = false;
});
document.addEventListener("touchmove", function () {
  dragged.value = true;
});
window.addEventListener("touchend", function (e) {
  if (dragged.value == true && e.changedTouches[0].pageX < oldX.value) {
    next();
  } else if (dragged.value == true && e.changedTouches[0].pageX > oldX.value) {
    back();
  }
});
</script>

<template>
  <div class="py-8 px-4 bg-white overflow-hidden">
    <div class="flex">
      <Slide
        v-for="(slide, idx) in slides"
        :key="idx"
        :slide="slide"
        :widthIndex="widthIndex"
      />
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
