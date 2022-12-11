<script lang="ts" setup>
import type { ISlide } from "@/interfaces/slide.interface";
import { computed, ref } from "vue";

const props = defineProps<{
  slide: ISlide;
  index: number;
  widthIndex: number;
}>();

const baseWidth = ref<Array<string>>([
  "min-w-[800px]",
  "min-w-[150px]",
  "min-w-[0px] mx-0",
]);

const width = computed(() => {
  if (props.index >= 1) {
    return [
      ...Array(props.index - 1).fill("min-w-[200px]"),
      ["min-w-[400px]"],
      ...baseWidth.value,
    ];
  }
  return baseWidth.value;
});

/*url('/src/assets/images/${props.slide.image}');*/
</script>

<template>
  <div
    :style="`background-image: url(${props.slide.image})`"
    class="h-[430px] bg-no-repeat bg-cover bg-center rounded-lg mx-4 animation-all ease-in-out duration-700"
    :class="width[widthIndex] ?? 'min-w-[0px] mx-0'"
  ></div>
</template>
