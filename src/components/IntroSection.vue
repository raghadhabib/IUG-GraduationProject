<template>
  <section
    class="relative w-full h-full flex items-center justify-center overflow-hidden"
  >
    <div
      class="absolute inset-0 bg-cover bg-center pointer-events-none"
    >
      <div class="absolute inset-0 z-0">
        <video
          ref="videoRef"
          autoplay
          muted
          loop
          playsinline
          class="w-full h-full object-cover opacity-50"
        >
          <source src="../assets/videos/Version1.mp4" type="video/mp4" />
        </video>
        <!-- dark overlay layer on video -->
        <div class="absolute inset-0 bg-black/20"></div> 
      </div>
    </div>

    <!-- Film Frame Image Overlay -->
    <img
      src="../assets/images/Vect"
      alt=""
      class="absolute inset-0 w-full h-full object-fill z-20 pointer-events-none"
    />

    <div class="relative z-10 text-center animate-[fadeInUp_1.5s_ease-out]">
      <h1
        class="text-4xl sm:text-8xl font-normal tracking-[2.4px] mb-4 text-white max-w-186 mx-auto"
      >
        Is Al-Ghazzawi a superhero?
      </h1>
      <p class="text-base sm:text-2xl text-white mb-12 font-normal max-w-190 leading-9.75">
        A cinematic journey through the resilience, humanity, and untold stories
        of Gaza
      </p>

      <!-- scroll indicator -->
      <div class="scroll-indicator" aria-hidden="false">
        <div class="mouse mb-2" role="img" aria-label="Scroll">
          <span class="mouse-wheel"></span>
        </div>
        <span class="scroll-label tracking-wider"> SCROLL TO EXPLORE </span>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from "vue";

const videoRef = ref(null);
const isMuted = ref(true);

const toggleMute = () => {
  isMuted.value = !isMuted.value;
  if (videoRef.value) {
    videoRef.value.muted = isMuted.value;
  }
};
</script>

<style scoped>
@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(50px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.scroll-indicator {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 10px;
  color: #ffffff;
  user-select: none;
  margin-top: 8px;
}

.mouse {
  width: 36px;
  height: 56px;
  border: 2px solid rgba(255, 255, 255, 0.9);
  border-radius: 20px;
  display: flex;
  align-items: flex-start;
  justify-content: center;
  padding-top: 8px;
  box-sizing: border-box;
  background: linear-gradient(180deg, rgba(255, 255, 255, 0.02), transparent);
  transition: transform 200ms ease, box-shadow 200ms ease;
  -webkit-backdrop-filter: blur(2px);
  backdrop-filter: blur(2px);
}

.mouse:hover {
  transform: translateY(-3px);
  box-shadow: 0 6px 20px rgba(0, 0, 0, 0.35);
}

.mouse-wheel {
  width: 4px;
  height: 10px;
  background: #ffffff;
  border-radius: 2px;
  opacity: 0.95;
  animation: wheelMove 1.4s infinite cubic-bezier(0.4, 0, 0.2, 1);
  transform-origin: center;
}

.scroll-label {
  font-size: 12px;
  letter-spacing: 2px;
  color: rgba(255, 255, 255, 0.6);
  font-weight: 500;
}

@keyframes wheelMove {
  0%   { transform: translateY(0);   opacity: 0.95; }
  40%  { transform: translateY(8px); opacity: 0.35; }
  80%  { transform: translateY(0);   opacity: 0.95; }
  100% { transform: translateY(0);   opacity: 0.95; }
}

@media (max-width: 640px) {
  .mouse       { width: 28px; height: 46px; border-radius: 16px; padding-top: 7px; }
  .mouse-wheel { height: 8px; width: 3px; }
  .scroll-label { font-size: 11px; letter-spacing: 1.6px; }
}
</style>