<template>
  <section
    class="relative pt-20 w-full h-full flex items-center justify-center overflow-hidden"
  >
    <div
      class="absolute inset-0 bg-cover bg-center pointer-events-none"
      :style="{ backgroundImage: `url(${storyBg})` }"
    />

    <!-- Content -->
    <div
      class="relative z-10 flex flex-col lg:flex-row max-w-350 w-[90%] gap-16 lg:gap-8 items-center px-8"
    >
      <!-- Text Content -->
      <div class="flex-1 animate-[slideInLeft_1s_ease-out]">
        <h2
          class="text-6xl lg:text-5xl font-normal mb-8 text-white [text-shadow:0_0_30px_rgba(212,175,55,0.4)]"
        >
          The Story
        </h2>

        <div class="flex flex-col gap-6 mb-6">
          <p
            class="text-lg lg:text-base leading-relaxed text-white/80 font-normal text-justify"
          >
            In the heart of one of the world's most contested territories,
            ordinary people live extraordinary lives. This documentary peels
            back the layers of headlines and history to reveal the human spirit
            that endures against all odds.
          </p>
          <p
            class="text-lg lg:text-base leading-relaxed text-white/80 font-normal text-justify"
          >
            Through intimate portraits and powerful testimonies, we witness
            stories of courage, creativity, and hope—a Gaza rarely seen, yet
            desperately needed to be told.
          </p>

          <p
            class="text-lg lg:text-base leading-relaxed text-white/80 font-normal text-justify"
          >
            From artists painting murals on rubble to children finding joy in
            the smallest moments, this is a testament to the indomitable will of
            humanity.
          </p>
        </div>

        <div
          class="w-24 h-0.5 bg-linear-to-r from-gold to-transparent mb-8"
        ></div>
        <button
          class="relative mt-8 px-10 py-3.5 text-sm tracking-[2px] uppercase bg-transparent border-2 border-gold text-gold transition-all duration-300 overflow-hidden group"
        >
          <span
            class="absolute inset-0 bg-gold -translate-x-full group-hover:translate-x-0 transition-transform duration-300 -z-10"
          ></span>
          <span class="relative group-hover:text-black">Read More</span>
        </button>
      </div>

      <!-- Image Content -->
      <div class="flex-1 animate-[slideInRight_1s_ease-out]">
        <div class="story-grid w-full flex items-center flex-col gap-3">
          <!-- Large top image -->
          <div class="story-img story-img-large rounded-lg overflow-hidden">
            <img :src="img1" alt="Scene 1" />
          </div>

          <!-- Two images side-by-side -->
          <div class="story-row mt-4 flex gap-4">
            <div class="story-img flex-1 rounded-lg overflow-hidden">
              <img :src="img2" alt="Scene 2" />
            </div>
            <div class="story-img flex-1 rounded-lg overflow-hidden">
              <img :src="img3" alt="Scene 3" />
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import storyBg from "../assets/images/story-bg.png";
import img1 from "../assets/images/store-section1.jpg";
import img2 from "../assets/images/story-section2.jpg";
import img3 from "../assets/images/story-section3.jpg";
// No props or reactive data needed for this component
</script>

<style scoped>
@keyframes slideInLeft {
  from {
    opacity: 0;
    transform: translateX(-100px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

@keyframes slideInRight {
  from {
    opacity: 0;
    transform: translateX(100px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

@keyframes shimmer {
  0% {
    transform: translate(-50%, -50%) rotate(0deg);
  }
  100% {
    transform: translate(-50%, -50%) rotate(360deg);
  }
}

/* Image grid styles */
.story-grid {
  display: block;
}

.story-img {
  height: 100%;
  background: rgba(0, 0, 0, 0.04);
}

.story-img img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
}

/* Large top image responsive heights */
.story-img-large {
  height: 320px;
}
@media (min-width: 1024px) {
  .story-img-large {
    height: 256px;
    width: 560px;
  }
  .story-row > .story-img {
    height: 160px;
    max-width: 272px;
  }
}
@media (max-width: 640px) {
  .story-img-large {
    height: 220px;
    width: auto; /* Adjust width for responsiveness */
  }
  .story-row {
    flex-direction: column;
  }
  .story-row > .story-img {
    height: 160px;
    width: auto; /* Adjust width for responsiveness */
  }
}
</style>
