<template>
  <section
    class="relative w-full h-full flex items-center justify-center overflow-hidden"
  >
    <div
      class="absolute inset-0 bg-cover bg-center pointer-events-none"
      :style="{ backgroundImage: `url(${storyBg})` }"
    />

    <!-- COLLAPSED layout (default) -->
    <div
      v-if="!isExpanded"
      class="relative z-10 flex flex-col lg:flex-row max-w-350 w-[90%] gap-16 lg:gap-8 items-center px-8 animate-[fadeIn_0.5s_ease-out]"
    >
      <!-- Text Content -->
      <div class="flex-1 animate-[slideInLeft_1s_ease-out]">
        <h2
          class="text-6xl lg:text-5xl font-normal mb-8 text-white [text-shadow:0_0_30px_rgba(212,175,55,0.4)]"
        >
          The Story
        </h2>

        <div class="flex flex-col gap-6 mb-6">
          <p class="text-lg lg:text-base leading-relaxed text-white/80 font-normal text-justify">
            After the crises that Gaza witnessed during the recent war, people from Gaza have come to be seen as superheroes.
But in reality, do they see themselves that way?

This film poses this question to three generations: a child, a young woman, and an elderly man, exploring how each of them views themselves and their reality.
          </p>
          <p class="text-lg lg:text-base leading-relaxed text-white/80 font-normal text-justify">
            The work documents part of the experience lived by people in Gaza and examines how challenge, hope, and faith can coexist at the same time.
          </p>
          <p class="text-lg lg:text-base leading-relaxed text-white/80 font-normal text-justify">
           A human journey that moves closer to the truth as seen through the eyes of those who lived it.
          </p>
        </div>

        <div class="w-24 h-0.5 bg-linear-to-r from-gold to-transparent mb-8"></div>
        <button
          @click="isExpanded = true"
          class="relative mt-8 px-10 py-3.5 text-sm tracking-[2px] uppercase border-2  bg-gold text-gold transition-all duration-300 overflow-hidden group cursor-pointer"
        >
          <span class="absolute inset-0 bg-gold -translate-x-full group-hover:translate-x-0 transition-transform duration-300 -z-10"></span>
          <span class="relative text-white">Read More</span>
        </button>
      </div>

      <!-- Image Content -->
      <div class="flex-1 animate-[slideInRight_1s_ease-out]">
        <div class="story-grid w-full flex items-center flex-col gap-3">
          <div class="story-img story-img-large  overflow-hidden">
            <img :src="img1" alt="Scene 1" class="story-photo" />
          </div>
          <div class="story-row mt-4 flex gap-4">
            <div class="story-img flex-1  overflow-hidden">
              <img :src="img2" alt="Scene 2" class="story-photo" />
            </div>
            <div class="story-img flex-1  overflow-hidden">
              <img :src="img3" alt="Scene 3" class="story-photo" />
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- EXPANDED layout -->
    <div
      v-else
      class="relative z-10 w-[90%] max-w-350 px-8 animate-[fadeIn_0.5s_ease-out]"
    >
      <h2
        class="text-6xl lg:text-5xl font-normal mb-10 text-white [text-shadow:0_0_30px_rgba(212,175,55,0.4)]"
      >
        The Story
      </h2>

      <div class="flex flex-col lg:flex-row gap-8 items-start">

        <div class="flex-1 flex flex-col gap-5">
          <p class="text-base leading-relaxed text-white/80 font-normal text-justify">
            In the heart of one of the world's most contested territories,
            ordinary people live extraordinary lives. This documentary peels
            back the layers of headlines and history to reveal the human spirit
            that endures against all odds.
          </p>
          <p class="text-base leading-relaxed text-white/80 font-normal text-justify">
            From artists painting murals on rubble to children finding joy in
            the smallest moments, this is a testament to the indomitable will of
            humanity.
          </p>
          <p class="text-base leading-relaxed text-white/80 font-normal text-justify">
            Through intimate portraits and powerful testimonies, we witness
            stories of courage, creativity, and hope—a Gaza rarely seen, yet
            desperately needed to be told.
          </p>
        </div>

        <div class="flex-1 flex flex-col gap-5">
          <p class="text-base leading-relaxed text-white/80 font-normal text-justify">
            In the heart of one of the world's most contested territories,
            ordinary people live extraordinary lives. This documentary peels
            back the layers of headlines and history to reveal the human spirit
            that endures against all odds.
          </p>
          <p class="text-base leading-relaxed text-white/80 font-normal text-justify">
            From artists painting murals on rubble to children finding joy in
            the smallest moments, this is a testament to the indomitable will of
            humanity.
          </p>
          <p class="text-base leading-relaxed text-white/80 font-normal text-justify">
            Through intimate portraits and powerful testimonies, we witness
            stories of courage, creativity, and hope—a Gaza rarely seen, yet
            desperately needed to be told.
          </p>
        </div>

        <div class="flex-1 flex flex-col gap-3">
          <div class=" overflow-hidden">
            <img :src="img1" alt="Scene 1" class="story-photo w-full h-48 object-cover" />
          </div>
          <div class="flex gap-3">
            <div class="flex-1  overflow-hidden">
              <img :src="img2" alt="Scene 2" class="story-photo w-full h-32 object-cover" />
            </div>
            <div class="flex-1  overflow-hidden">
              <img :src="img3" alt="Scene 3" class="story-photo w-full h-32 object-cover" />
            </div>
          </div>
        </div>

      </div>

      <div class="w-24 h-0.5 bg-linear-to-r from-gold to-transparent mt-8 mb-6 ml-auto"></div>
      <div class="flex justify-end">
        <button
          @click="isExpanded = false"
          class="relative px-10 py-3.5 text-sm tracking-[2px] uppercase border-2 bg-gold text-gold transition-all duration-300 overflow-hidden group cursor-pointer"
        >
          <span class="absolute inset-0 bg-gold -translate-x-full group-hover:translate-x-0 transition-transform duration-300 -z-10"></span>
          <span class="relative text-white">Read Less</span>
        </button>
      </div>
    </div>

  </section>
</template>

<script setup>
import { ref } from "vue";
import storyBg from "../assets/images/story-bg.png";
import img1 from "../assets/images/sea.png";
import img2 from "../assets/images/bird.jpeg";
import img3 from "../assets/images/flowerWithBuilding.jpeg";

const isExpanded = ref(false);
</script>

<style scoped>
@keyframes fadeIn {
  from { opacity: 0; transform: translateY(16px); }
  to   { opacity: 1; transform: translateY(0); }
}

@keyframes slideInLeft {
  from { opacity: 0; transform: translateX(-100px); }
  to   { opacity: 1; transform: translateX(0); }
}

@keyframes slideInRight {
  from { opacity: 0; transform: translateX(100px); }
  to   { opacity: 1; transform: translateX(0); }
}

/* Grayscale hover effect */
.story-photo {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
  filter: grayscale(0%);
  transition: filter 0.4s ease;
}

.story-photo:hover {
  filter: grayscale(100%);
}

/* Image grid styles */
.story-grid { display: block; }
.story-img { height: 100%; background: rgba(0,0,0,0.04); }

.story-img-large { height: 320px; }

@media (min-width: 1024px) {
  .story-img-large { height: 256px; width: 560px; }
  .story-row > .story-img { height: 160px; max-width: 272px; }
}

@media (max-width: 640px) {
  .story-img-large { height: 220px; width: auto; }
  .story-row { flex-direction: column; }
  .story-row > .story-img { height: 160px; width: auto; }
}
</style>