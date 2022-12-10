<script lang="ts" setup>
const props = defineProps<{
  image: string;
}>();
</script>

<template>
  <div
    :style="`background-image: url('/src/assets/images/${props.image}');`"
    class="min-w-[500px] h-[430px] bg-center bg-cover bg-no-repeat rounded-lg mx-4"
  ></div>
</template>
