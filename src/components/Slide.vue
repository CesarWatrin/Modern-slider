<script lang="ts" setup>
interface ISlide {
  image: string;
  width: Array<string>;
}

const props = defineProps<{
  slide: ISlide;
  widthIndex: number;
}>();

/*url('/src/assets/images/${props.slide.image}');*/
</script>

<template>
  <div
    :style="`background-image: url('/src/assets/images/${props.slide.image}'); #000000`"
    class="h-[430px] bg-no-repeat bg-cover bg-center rounded-lg mx-4 animation-all ease-in-out duration-1000"
    :class="props.slide.width[widthIndex] ?? 'min-w-[0px] mx-0'"
  ></div>
</template>
