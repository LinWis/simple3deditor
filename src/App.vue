<script setup lang="ts">
import MainControl from "./components/MainControl.vue";
import MainScene from "./components/MainScene.vue";
import MainHeader from "./components/MainHeader.vue";
import MainFooter from "./components/MainFooter.vue";

</script>

<template>
  <div class="w-screen h-screen">
    <MainHeader />
    <div class="w-full">
      <MainScene />
      <MainControl />
    </div>
    <MainFooter />
  </div>
</template>

<style scoped>
</style>
