<script lang="ts" setup>
import type { ISlide } from "@/interfaces/slide.interface";

const props = defineProps<{
  slide: ISlide;
  widthIndex: number;
}>();

/*url('/src/assets/images/${props.slide.image}');*/
</script>

<template>
  <div
    :style="`background: #000000`"
    class="h-[430px] bg-no-repeat bg-cover bg-center rounded-lg mx-4 animation-all ease-in-out duration-700"
    :class="props.slide.width[widthIndex] ?? 'min-w-[0px] mx-0'"
  ></div>
</template>
