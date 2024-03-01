<script setup lang="ts">
  import { ref } from 'vue';

  const showSidebar = ref(false);

  function addMesh() {
    
  }

</script>

<template>
  <Transition name="slide-btn">
    <button 
      v-if="!showSidebar"
      class="fixed right-0 text-white"
      @click="showSidebar = !showSidebar"
    >
      <img
        width="40px"
        src="../assets/left-arrow.svg"
      >
    </button>  
  </Transition>

  <Transition name="slide-fade">
    <div
      v-if="showSidebar"
      class="w-2/12 min-h-full bg-zinc-950 overflow-hidden text-white fixed right-0 items-center flex flex-col justify-between py-10"
    >
      <div class="control__header w-full text-left px-5">
        <button @click="showSidebar =!showSidebar">
          <img 
            width="35px"
            src="../assets/left-arrow-line.svg"
          >
        </button>
        <div class="add-mesh flex justify-center">
          <button 
            class="bg-zinc-900 p-2 rounded-md hover:bg-zinc-800"
            @click="addMesh"
          >
            Add mesh
          </button>
        </div>
      </div>
      <div class="control__content">
        content
      </div>
      <div class="control__footer">
        footer
      </div>
    </div>
  </Transition>
</template>

<style scoped>
  .slide-fade-enter-active {
    transition: all 0.6s ease-out;
  }

  .slide-fade-leave-active {
    transition: all 0.6s cubic-bezier(1, 0.5, 0.8, 1);
  }

  .slide-btn-enter-from, .slide-btn-leave-active {
    opacity: 100%;
  }

  .slide-btn-enter-active, .slide-btn-leave-from {
    transition: all 0.5s linear;
    opacity: 0;
  }


  .slide-fade-enter-from, .slide-fade-leave-to {
    transform: translateX(20px);
    opacity: 0;
  }
</style>