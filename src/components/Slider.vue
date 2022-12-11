<script lang="ts" setup>
import { ref } from "vue";
import Slide from "@/components/Slide.vue";
import type { ISlide } from "@/interfaces/slide.interface";

const slides = ref<Array<ISlide>>([
  {
    image:
      "https://images.pexels.com/photos/2662116/pexels-photo-2662116.jpeg?auto=compress&cs=tinysrgb&dpr=1&w=500",
  },
  {
    image:
      "https://www.adorama.com/alc/wp-content/uploads/2018/11/landscape-photography-tips-yosemite-valley-feature.jpg",
  },
  {
    image:
      "https://petapixel.com/assets/uploads/2022/08/fdfs19-800x533.jpg",
  },
  {
    image:
      "https://i.natgeofe.com/n/2a832501-483e-422f-985c-0e93757b7d84/6.jpg?w=636&h=477",
  },
  {
    image:
      "https://petapixel.com/assets/uploads/2022/08/fdfs17-800x533.jpg",
  },
  {
    image:
      "https://assets.photographycourse.net/wp-content/uploads/2022/04/12225324/Portrait-vs-Landscape-Featured-Image-3.jpg",
  },
  {
    image:
      "https://thumbs.dreamstime.com/b/romanian-hillside-village-summer-time-mountain-landscape-transylvania-romania-romanian-hillside-village-summer-120917479.jpg",
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
        :index="idx"
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
