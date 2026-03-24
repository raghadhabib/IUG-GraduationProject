<template>
  <section class="relative min-h-screen overflow-hidden bg-black flex flex-col items-center justify-center">
    <div
      class="absolute inset-0 z-0 bg-cover bg-center bg-no-repeat"
      :style="{ backgroundImage: `url(${filmBg})` }"
    >
      <div class="absolute inset-0 bg-black/70"></div>
    </div>

    <div class="relative z-10 w-full flex flex-col items-center justify-center px-4 md:px-8">
      <div class="relative w-full max-w-[90vw] md:max-w-[800px] lg:max-w-[1000px] aspect-video">

        <iframe
          v-if="isPlaying"
          class="absolute inset-0 w-full h-full"
          src="https://www.youtube.com/embed/ivP-1oSuQxc?si=aZqw_dLoDBO9mUUj&autoplay=1"
          title="YouTube video player"
          frameborder="0"
          allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
          referrerpolicy="strict-origin-when-cross-origin"
          allowfullscreen
        ></iframe>

        <div v-else class="absolute inset-0 flex flex-col items-center justify-center">
          <button
            @click="isPlaying = true"
            class="group relative w-16 h-16 md:w-20 md:h-20 flex items-center justify-center rounded-full border-2 border-white bg-white hover:bg-white/20 transition-all duration-500"
          >
            <div class="w-0 h-0 border-t-[14px] border-t-transparent border-l-[24px] border-l-[#B8860B] border-b-[14px] border-b-transparent ml-1.5 md:border-t-[18px] md:border-l-[30px] md:border-b-[18px] md:ml-2"></div>
            <div class="absolute inset-0 rounded-full border border-white animate-ping opacity-20"></div>
          </button>

          <div class="mt-4 md:mt-6 text-center">
            <span class="block text-white text-sm md:text-lg tracking-[4px] mb-1">Click To Watch Film</span>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
<script setup>
import { ref } from 'vue';
import filmBg from '../assets/images/thumnail.webp'
const isPlaying = ref(false);
</script>

<style scoped>
.text-gold { color: #d4af37; }
.border-gold { border-color: #d4af37; }
.bg-gold { background-color: #d4af37; }
</style>
