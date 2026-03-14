<template>
  <section
    class="relative w-full h-full flex items-center justify-center overflow-hidden"
  >
    <div class="absolute inset-0 bg-cover bg-center pointer-events-none">
      <div class="absolute inset-0 z-0">
        <video
          ref="videoRef"
          autoplay
          muted
          loop
          playsinline
          class="w-full h-full object-cover opacity-50"
          poster="../assets/images/bird.jpeg"
        >
          <source src="../assets/videos/finalVersion.webm" type="video/webm">
        </video>
        <div class="absolute inset-0 bg-black/40"></div>
      </div>
    </div>

    <div class="relative z-10 text-center animate-[fadeInUp_1.5s_ease-out]">
      <h1 class="text-4xl sm:text-8xl font-normal tracking-[2.4px] mb-8 text-white max-w-186 mx-auto">
        Is Al-Ghazzawi a superhero?
      </h1>
      <p class="text-base sm:text-2xl text-white mb-8 font-normal max-w-190 leading-9.75 px-6 sm:px-0">
        A cinematic journey through the resilience, humanity, and untold stories of Gaza
      </p>
      <p class="text-xs sm:text-xl text-white/80 mb-8 font-normal max-w-190 leading-9.75 px-6 sm:px-0">Real .Documentary .Short film</p>

      <!-- Desktop: mouse scroll indicator -->
      <div class="scroll-indicator hidden sm:flex" aria-hidden="true">
        <div class="mouse mb-2" role="img" aria-label="Scroll">
          <span class="mouse-wheel"></span>
        </div>
        <span class="scroll-label tracking-wider">SCROLL TO EXPLORE</span>
      </div>

      <!-- Mobile: two SVGs crossfading, moving only downward -->
      <div class="swipe-indicator flex sm:hidden" aria-label="Swipe to explore">
        <div class="svgs-wrap">

          <!-- State 1: finger pointing left -->
          <svg class="finger-state state-1" width="47" height="42" viewBox="0 0 47 42" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M42.1382 27.8268L38.1672 17.7295C37.5908 16.2638 36.0124 15.4608 34.4851 15.8465L27.3925 17.6553L25.5077 12.8626C24.7528 10.9432 22.5648 9.99035 20.6454 10.7452C18.726 11.5 17.7732 13.6881 18.528 15.6075L22.8192 26.519L22.0118 26.447C19.8124 26.2508 17.8123 27.7225 17.3447 29.8808L17.2398 30.3653C17.1688 30.6879 17.1625 31.0214 17.2212 31.3464C17.2799 31.6715 17.4024 31.9817 17.5816 32.2591C17.9358 32.8183 18.5069 33.2116 19.1514 33.3476L26.7438 34.9957C26.9831 35.0485 27.2327 35.0298 27.4614 34.9419L41.4324 29.4475C42.0722 29.1959 42.3898 28.4666 42.1382 27.8268ZM26.9071 32.4735L19.6832 30.9088L19.7882 30.4243C19.9885 29.4992 20.8418 28.8682 21.7883 28.9526L24.6118 29.1988C25.0411 29.2315 25.4669 29.0506 25.7219 28.7085C25.8484 28.5378 25.9292 28.3377 25.9568 28.1271C25.9845 27.9165 25.9579 27.7023 25.8798 27.5047L20.8475 14.7087C20.5959 14.0689 20.9135 13.3396 21.5533 13.088C22.1931 12.8363 22.9224 13.1539 23.174 13.7938L25.4615 19.6101C25.6902 20.1918 26.329 20.5181 26.938 20.3592L35.1046 18.2758C35.4092 18.1963 35.7263 18.3537 35.8452 18.6561L39.3587 27.5901L26.9116 32.4851L26.9071 32.4735Z" fill="white"/>
            <path d="M14.1565 3.73842C14.3243 3.39014 14.178 2.97176 13.8297 2.80395L8.15416 0.0693233C7.80588 -0.0984871 7.3875 0.0478117 7.21969 0.396091C7.05188 0.744371 7.19818 1.16274 7.54646 1.33056L12.5914 3.76134L10.1606 8.80627C9.99279 9.15455 10.1391 9.57292 10.4874 9.74073C10.8357 9.90854 11.254 9.76224 11.4218 9.41396L14.1565 3.73842ZM5.88682 24.0483C6.22577 24.2342 6.65127 24.1102 6.83722 23.7712L9.86732 18.2478C10.0533 17.9089 9.92923 17.4833 9.59028 17.2974C9.25134 17.1115 8.82583 17.2355 8.63989 17.5744L5.94646 22.4842L1.03673 19.7908C0.697784 19.6048 0.272278 19.7288 0.0863357 20.0678C-0.0996065 20.4067 0.0244279 20.8322 0.363374 21.0182L5.88682 24.0483ZM13.5259 3.43457L13.2948 2.7738C8.19588 4.55682 5.31907 6.92158 4.2495 10.4173C3.20654 13.826 3.95043 18.138 5.55147 23.6305L6.2235 23.4346L6.89553 23.2387C5.2901 17.7311 4.68065 13.7931 5.58824 10.8269C6.46922 7.94756 8.84682 5.81232 13.7569 4.09534L13.5259 3.43457Z" fill="white"/>
          </svg>

          <!-- State 2: finger pointing up/forward -->
          <svg class="finger-state state-2" width="47" height="42" viewBox="0 0 47 42" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M40.612 13.3183L30.1581 10.4133C28.6406 9.99159 27.0494 10.7689 26.4383 12.2208L23.6147 18.9739L18.6527 17.595C16.6655 17.0428 14.5878 18.2168 14.0356 20.204C13.4834 22.1912 14.6574 24.269 16.6446 24.8212L27.9416 27.9605L27.3982 28.5619C25.9179 30.2004 25.8896 32.6835 27.332 34.3557L27.6558 34.7311C27.8708 34.982 28.1333 35.1877 28.4282 35.3364C28.7231 35.4852 29.0446 35.574 29.374 35.5978C30.0337 35.6514 30.6915 35.432 31.188 34.9992L37.0734 29.9272C37.2595 29.7679 37.3947 29.5573 37.4622 29.3217L41.4817 14.8573C41.6657 14.1949 41.2744 13.5024 40.612 13.3183ZM35.1572 28.279L29.5603 33.1067L29.2365 32.7313C28.6183 32.0147 28.6278 30.9535 29.2648 30.2483L31.1606 28.1414C31.445 27.8183 31.5568 27.3693 31.4371 26.9598C31.3768 26.7561 31.2657 26.5711 31.1141 26.4223C30.9625 26.2735 30.7755 26.1658 30.5707 26.1093L17.3227 22.4278C16.6603 22.2438 16.2689 21.5512 16.453 20.8888C16.6371 20.2264 17.3296 19.835 17.992 20.0191L24.0139 21.6925C24.616 21.8598 25.2611 21.5461 25.5007 20.964L28.7514 13.1879C28.8712 12.8969 29.1877 12.7383 29.5008 12.8254L38.7503 15.3957L35.1692 28.2824L35.1572 28.279Z" fill="white"/>
            <path d="M14.1565 3.73842C14.3243 3.39014 14.178 2.97176 13.8297 2.80395L8.15416 0.0693233C7.80588 -0.0984871 7.3875 0.0478117 7.21969 0.396091C7.05188 0.744371 7.19818 1.16274 7.54646 1.33056L12.5914 3.76134L10.1606 8.80627C9.99279 9.15455 10.1391 9.57292 10.4874 9.74073C10.8357 9.90854 11.254 9.76224 11.4218 9.41396L14.1565 3.73842ZM5.88682 24.0483C6.22577 24.2342 6.65127 24.1102 6.83722 23.7712L9.86732 18.2478C10.0533 17.9089 9.92923 17.4833 9.59028 17.2974C9.25134 17.1115 8.82583 17.2355 8.63989 17.5744L5.94646 22.4842L1.03673 19.7908C0.697784 19.6048 0.272278 19.7288 0.0863357 20.0678C-0.0996065 20.4067 0.0244279 20.8322 0.363374 21.0182L5.88682 24.0483ZM13.5259 3.43457L13.2948 2.7738C8.19588 4.55682 5.31907 6.92158 4.2495 10.4173C3.20654 13.826 3.95043 18.138 5.55147 23.6305L6.2235 23.4346L6.89553 23.2387C5.2901 17.7311 4.68065 13.7931 5.58824 10.8269C6.46922 7.94756 8.84682 5.81232 13.7569 4.09534L13.5259 3.43457Z" fill="white"/>
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
   MOBILE — SVGs crossfade, move only downward (Y)
══════════════════════════════════════════════════ */
.swipe-indicator {
  flex-direction: column;
  align-items: center;
  gap: 12px;
  margin-top: 8px;
  user-select: none;
}

.svgs-wrap {
  position: relative;
  width: 56px;
  height: 50px;
}

.finger-state {
  position: absolute;
  top: 0;
  left: 0;
  width: 56px;
  height: 50px;
  filter: drop-shadow(0 2px 8px rgba(0, 0, 0, 0.45));
}

/*
  Cycle: 4s
  0%  – 30%  → state-1 visible, moves downward
  30% – 45%  → state-1 fades out downward / state-2 fades in from above
  45% – 75%  → state-2 visible, moves downward
  75% – 90%  → state-2 fades out downward / state-1 fades in from above
  90% – 100% → state-1 settling
*/

.state-1 {
  animation: state1Anim 4s cubic-bezier(0.45, 0, 0.55, 1) infinite;
}
.state-2 {
  animation: state2Anim 4s cubic-bezier(0.45, 0, 0.55, 1) infinite;
}

@keyframes state1Anim {
  0%   { opacity: 1;   transform: translateY(0px);   }
  30%  { opacity: 1;   transform: translateY(8px);   }
  45%  { opacity: 0;   transform: translateY(14px);  }
  75%  { opacity: 0;   transform: translateY(-8px);  }
  90%  { opacity: 0;   transform: translateY(-4px);  }
  100% { opacity: 1;   transform: translateY(0px);   }
}

@keyframes state2Anim {
  0%   { opacity: 0;   transform: translateY(-8px);  }
  30%  { opacity: 0;   transform: translateY(-8px);  }
  45%  { opacity: 1;   transform: translateY(0px);   }
  75%  { opacity: 1;   transform: translateY(8px);   }
  90%  { opacity: 0;   transform: translateY(14px);  }
  100% { opacity: 0;   transform: translateY(-8px);  }
}

.swipe-label {
  font-size: 11px;
  letter-spacing: 2px;
  color: rgba(255,255,255,0.55);
  font-weight: 500;
}
</style>