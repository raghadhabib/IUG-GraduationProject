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
         <source src="../assets/videos/finalVersion.webm" type="video/webm">
        </video>
        <div class="absolute inset-0 bg-black/40"></div> 
      </div>
    </div>

    <div class="relative z-10 text-center animate-[fadeInUp_1.5s_ease-out]">
      <h1
        class="text-4xl sm:text-8xl font-normal tracking-[2.4px] mb-8 text-white max-w-186 mx-auto"
      >
        Is Al-Ghazzawi a superhero?
      </h1>
      <p class="text-base sm:text-2xl text-white mb-8 font-normal max-w-190 leading-9.75 px-6 sm:px-0">
        A cinematic journey through the resilience, humanity, and untold stories
        of Gaza
      </p>
      <p class="text-xs sm:text-xl text-white/80 mb-8 font-normal max-w-190 leading-9.75 px-6 sm:px-0">Real .Documentary .Short film</p>

      <!-- Desktop: mouse scroll indicator -->
      <div class="scroll-indicator hidden sm:flex" aria-hidden="true">
        <div class="mouse mb-2" role="img" aria-label="Scroll">
          <span class="mouse-wheel"></span>
        </div>
        <span class="scroll-label tracking-wider">SCROLL TO EXPLORE</span>
      </div>

      <!-- Mobile: finger swipe up indicator -->
      <div class="swipe-indicator flex sm:hidden" aria-label="Swipe to explore">
        <div class="finger-wrap">
          <!-- Ripple rings -->
          <span class="ripple ripple-1"></span>
          <span class="ripple ripple-2"></span>

          <!-- Finger SVG -->
          <svg
            class="finger-icon"
            viewBox="0 0 40 56"
            fill="none"
            xmlns="http://www.w3.org/2000/svg"
          >
            <!-- palm -->
            <rect x="12" y="28" width="16" height="20" rx="8" fill="white" opacity="0.95"/>
            <!-- index finger -->
            <rect x="16" y="10" width="8" height="24" rx="4" fill="white" opacity="0.95"/>
            <!-- swipe arrow chevrons -->
            <polyline points="15,7 20,2 25,7" stroke="white" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" opacity="0.7"/>
            <polyline points="15,13 20,8 25,13" stroke="white" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" opacity="0.35"/>
          </svg>
        </div>
        <span class="swipe-label">SWIPE TO EXPLORE</span>
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
/* ── Shared fadeInUp ───────────────────────────── */
@keyframes fadeInUp {
  from { opacity: 0; transform: translateY(50px); }
  to   { opacity: 1; transform: translateY(0); }
}

/* ══════════════════════════════════════════════════
   DESKTOP — mouse scroll indicator
══════════════════════════════════════════════════ */
.scroll-indicator {
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
  border: 2px solid rgba(255,255,255,0.9);
  border-radius: 20px;
  display: flex;
  align-items: flex-start;
  justify-content: center;
  padding-top: 8px;
  box-sizing: border-box;
  background: linear-gradient(180deg, rgba(255,255,255,0.02), transparent);
  transition: transform 200ms ease, box-shadow 200ms ease;
  backdrop-filter: blur(2px);
}

.mouse:hover {
  transform: translateY(-3px);
  box-shadow: 0 6px 20px rgba(0,0,0,0.35);
}

.mouse-wheel {
  width: 4px;
  height: 10px;
  background: #ffffff;
  border-radius: 2px;
  opacity: 0.95;
  animation: wheelMove 1.4s infinite cubic-bezier(0.4, 0, 0.2, 1);
}

.scroll-label {
  font-size: 12px;
  letter-spacing: 2px;
  color: rgba(255,255,255,0.6);
  font-weight: 500;
}

@keyframes wheelMove {
  0%   { transform: translateY(0);   opacity: 0.95; }
  40%  { transform: translateY(8px); opacity: 0.35; }
  80%  { transform: translateY(0);   opacity: 0.95; }
  100% { transform: translateY(0);   opacity: 0.95; }
}

/* ══════════════════════════════════════════════════
   MOBILE — finger swipe indicator
══════════════════════════════════════════════════ */
.swipe-indicator {
  flex-direction: column;
  align-items: center;
  gap: 12px;
  margin-top: 8px;
  user-select: none;
}

.finger-wrap {
  position: relative;
  width: 56px;
  height: 56px;
  display: flex;
  align-items: center;
  justify-content: center;
}

/* the finger bobs upward on repeat */
.finger-icon {
  width: 36px;
  height: 50px;
  animation: fingerSwipe 1.8s ease-in-out infinite;
  position: relative;
  z-index: 2;
  filter: drop-shadow(0 2px 8px rgba(0,0,0,0.4));
}

@keyframes fingerSwipe {
  0%   { transform: translateY(8px);  opacity: 0.5; }
  30%  { transform: translateY(-10px); opacity: 1;   }
  60%  { transform: translateY(-10px); opacity: 1;   }
  100% { transform: translateY(8px);  opacity: 0.5; }
}

/* ripple rings that expand outward */
.ripple {
  position: absolute;
  border-radius: 50%;
  border: 1.5px solid rgba(255,255,255,0.4);
  animation: rippleOut 1.8s ease-out infinite;
  pointer-events: none;
}

.ripple-1 {
  width: 36px;
  height: 36px;
  animation-delay: 0s;
}

.ripple-2 {
  width: 36px;
  height: 36px;
  animation-delay: 0.5s;
}

@keyframes rippleOut {
  0%   { transform: scale(0.6); opacity: 0.6; }
  100% { transform: scale(2.2); opacity: 0;   }
}

.swipe-label {
  font-size: 11px;
  letter-spacing: 2px;
  color: rgba(255,255,255,0.55);
  font-weight: 500;
}
</style>