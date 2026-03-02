<template>
  <section class="relative w-full h-full overflow-hidden bg-black">
  <div 
    class="absolute inset-0 z-0 bg-cover bg-center bg-no-repeat"
    :style="{ backgroundImage: `url(${filmBg})` }"
  >
    <div class="absolute inset-0 bg-black/40"></div>
  </div>

    

    <div class="relative z-10 w-full h-full flex flex-col items-center justify-center px-8">
      <div class="relative w-full max-w-[1000px] aspect-video group">
        
        <iframe
          v-if="isPlaying"
          class="absolute inset-0 w-full h-full rounded-lg shadow-2xl"
          src="https://www.youtube.com/embed/-VectWsWc1Q?autoplay=1&mute=0"
          frameborder="0"
          allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
          allowfullscreen
        ></iframe>

        <div v-else class="absolute inset-0 flex flex-col items-center justify-center">
          <button 
            @click="isPlaying = true"
            class="group relative w-28 h-28 flex items-center justify-center rounded-full border-2 border-white bg-white hover:bg-white/20 transition-all duration-500"
          >
            <div class="w-0 h-0 border-t-[18px] border-t-transparent border-l-[30px] border-l-[#FF5524] border-b-[18px] border-b-transparent ml-2"></div>
            
            <div class="absolute inset-0 rounded-full border border-white animate-ping opacity-20"></div>
          </button>
          
          <div class="mt-6 text-center">
            <span class="block text-white text-xs tracking-[4px] uppercase mb-1">Click to Watch Film</span>
            <span class="block text-white/40 text-[10px] tracking-[2px] uppercase">Full documentary available now </span>
          </div>
        </div> 
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue';
import filmBg from '../assets/images/story-bg.png'

const isPlaying = ref(false);

const shareLink = () => {
  if (navigator.share) {
    navigator.share({
      title: 'Is Al-Ghazzawi a superhero?',
      url: window.location.href
    });
  } else {
    // Fallback for browsers that don't support native share
    navigator.clipboard.writeText(window.location.href);
    alert('Link copied to clipboard!');
  }
};
</script>

<style scoped>
/* Gold color to match your palette */
.text-gold { color: #d4af37; }
.border-gold { border-color: #d4af37; }
.bg-gold { background-color: #d4af37; }
</style>