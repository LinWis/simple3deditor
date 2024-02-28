<script setup lang="ts">
import MainControl from "./components/MainControl.vue";
import MainScene from "./components/MainScene.vue";
import MainHeader from "./components/MainHeader.vue";
// import MainFooter from "./components/MainFooter.vue";

</script>

<template>
  <MainHeader />
  <div class="w-full h-full flex flex-row items-center">
    <MainScene />
    <MainControl />
  </div>
  <!-- <MainFooter /> -->
</template>

<style scoped>
</style>
