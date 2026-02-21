<template>
  <section class="relative w-full h-full overflow-hidden bg-black">
    <div class="absolute inset-0 z-0">
     <img src="../assets/images/story-bg.png" class="h-full">
      <div class="absolute inset-0 bg-black/40"></div>
    </div>

    <button 
      @click="shareLink"
      class="absolute top-10 right-10 z-30 flex items-center gap-2 px-4 py-2 bg-white/10 hover:bg-white/20 backdrop-blur-md border border-white/20 rounded-full text-white text-xs tracking-widest transition-all uppercase"
    >
      <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M4 12v8a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2v-8"/><polyline points="16 6 12 2 8 6"/><line x1="12" y1="2" x2="12" y2="15"/></svg>
      SHARE
    </button>

    <div class="relative z-10 w-full h-full flex flex-col items-center justify-center px-8">
      <!-- <h2 class="text-6xl md:text-7xl font-serif text-white mb-2 tracking-tight">
        Is Al-Ghazzawi a superhero?
      </h2>
      <p class="text-white/70 text-sm tracking-[3px] mb-12 uppercase">
        Experience the complete journey. Watch the stories unfold.
      </p> -->

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
            class="group relative w-24 h-24 flex items-center justify-center rounded-full border-2 border-gold/60 bg-gold/10 hover:bg-gold/20 transition-all duration-500"
          >
            <div class="w-0 h-0 border-t-[12px] border-t-transparent border-l-[20px] border-l-gold border-b-[12px] border-b-transparent ml-2"></div>
            
            <div class="absolute inset-0 rounded-full border border-gold animate-ping opacity-20"></div>
          </button>
          
          <div class="mt-6 text-center">
            <span class="block text-white text-xs tracking-[4px] uppercase mb-1">Click to Watch Trailer</span>
            <span class="block text-white/40 text-[10px] tracking-[2px] uppercase">Full documentary available soon</span>
          </div>
        </div> 
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue';

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