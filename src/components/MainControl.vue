<script setup lang="ts">
import { ref } from 'vue';

  const showSidebar = ref(false);
</script>

<template>
  <button 
    :class="{'fixed right-0 text-white': !showSidebar}"
    @click="showSidebar = !showSidebar"
  >
    <img
      width="40px"
      src="../assets/left-arrow.svg"
    >
  </button>  
  <div
    class="w-2/12 min-h-full bg-zinc-950 overflow-hidden text-white fixed right-0 items-center flex-col justify-between py-10"
    :class="{'flex': showSidebar, 'hidden': !showSidebar}"
  >
    <div class="control__header w-full text-left px-5">
      <button @click="showSidebar =!showSidebar">
        <img 
          width="35px"
          src="../assets/left-arrow-line.svg"
        >
      </button>
    </div>
    <div class="control__content">
      content
    </div>
  </div>
</template>

<style scoped lang="">
</style>