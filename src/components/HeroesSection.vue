<template>
  <section
    class="relative pt-20 w-full h-full flex items-start justify-center overflow-hidden bg-black"
  >
    <div class="relative z-10 max-w-350 w-[90%] px-8 py-16 mx-auto">

      <h2 class="text-6xl lg:text-5xl md:text-4xl font-normal text-white mb-4">
        The Heroes
      </h2>
      <p class="text-xl md:text-lg text-white/70 mb-2 font-normal max-w-165">
        Meet the extraordinary individuals whose courage and resilience
        illuminate the true spirit of Gaza.
      </p>

      <!-- ─── CARD GRID VIEW ─── -->
      <div v-if="!detailView" class="relative mt-10">

        <!-- Desktop: 3 equal cards -->
        <div class="hidden md:grid grid-cols-3 gap-6">
          <div
            v-for="(hero, index) in getCurrentSlideHeroes"
            :key="index"
            class="group relative bg-black overflow-hidden cursor-pointer"
          >
            <div class="relative w-full h-[380px] overflow-hidden">
              <img
                :src="hero.image"
                :alt="hero.name"
                class="w-full h-full object-cover object-top transition-transform duration-500 ease-in-out group-hover:scale-105"
              />
              <div
                class="absolute inset-0 bg-gradient-to-t from-black/95 via-black/60 to-black/10 transition-all duration-500 group-hover:from-black group-hover:via-black/90 group-hover:to-black/70"
              ></div>
              <div class="absolute bottom-0 left-0 right-0 p-6 pb-7 text-white">
                <p class="text-yellow-600 text-xs uppercase tracking-wider mb-2 font-medium">
                  {{ hero.role }}
                </p>
                <h3 class="text-2xl font-light leading-tight">{{ hero.name }}</h3>

                <!-- Description slides in on hover -->
                <div
                  class="max-h-0 opacity-0 group-hover:max-h-40 group-hover:opacity-100 overflow-hidden transition-all duration-500 ease-in-out mb-0 group-hover:mb-3  rounded px-3 py-2"
                >
                  <p class="text-white/85 text-sm leading-relaxed">{{ hero.description }}</p>
                </div>

                <!-- Quote with gold border on hover -->
                <div class="transition-all duration-300 group-hover:border-l-2 group-hover:border-yellow-600 group-hover:pl-3">
                  <p class="text-white/75 italic text-sm leading-relaxed">{{ hero.quote }}</p>
                </div>
              </div>
            </div>
          </div>
        </div>

        <!-- Gold NEXT arrow only (no prev arrow) -->
        <button
          class="hidden md:flex absolute top-1/2 -right-7 transform -translate-y-1/2 z-20
                 bg-yellow-600 hover:bg-yellow-500 text-black w-14 h-14 rounded-full text-2xl
                 cursor-pointer items-center justify-center transition-all duration-300
                 hover:scale-110 shadow-[0_0_20px_rgba(212,175,55,0.5)]"
          @click="openDetail"
          aria-label="View more"
        >
          ›
        </button>

        <!-- Mobile list -->
        <div class="md:hidden flex flex-col gap-8 mt-8">
          <div v-for="(hero, index) in allHeroes" :key="index" class="relative group">
            <div class="relative w-full h-[400px] overflow-hidden rounded-lg">
              <img
                :src="hero.image"
                :alt="hero.name"
                class="w-full h-full object-cover transition-transform duration-500 group-hover:scale-105"
              />
              <div class="absolute inset-0 bg-gradient-to-t from-black/90 via-black/60 to-transparent"></div>
              <div class="absolute bottom-0 left-0 right-0 p-6">
                <p class="text-yellow-600 text-xs uppercase tracking-wider mb-2 font-medium">{{ hero.role }}</p>
                <h3 class="text-3xl font-light text-white mb-2">{{ hero.name }}</h3>
                <p class="text-white/80 italic text-sm leading-relaxed">{{ hero.quote }}</p>
              </div>
            </div>
          </div>
        </div>

      </div>

      <!-- ─── DETAIL / FULL-WIDTH VIEW ─── -->
      <div v-else class="mt-8 animate-[fadeIn_0.6s_ease-out]">

        <!-- Full-width image with overlay text -->
        <div class="relative w-full rounded-sm" style="overflow: visible;">

          <!-- Back arrow — gold, center-left, forced above image -->
          <button
            @click="closeDetail"
            class="absolute top-1/2 -left-7 -translate-y-1/2 flex items-center justify-center
                   w-14 h-14 rounded-full bg-yellow-600 hover:bg-yellow-500
                   text-black text-2xl transition-all duration-300
                   hover:scale-110 shadow-[0_0_20px_rgba(212,175,55,0.5)]"
            style="z-index: 50;"
            aria-label="Back to heroes"
          >
            ‹
          </button>

          <img
            :src="detailHero.landscapeImage || detailHero.image"
            :alt="detailHero.name"
            class="w-full h-[65vh] object-cover object-center"
          />

          <!-- Bottom gradient -->
          <div class="absolute inset-0 bg-gradient-to-t from-black/90 via-black/30 to-transparent"></div>

          <!-- Name + quote at bottom center -->
          <div class="absolute bottom-0 left-0 right-0 pb-8 px-8 text-center text-white">
            <h3 class="text-4xl font-light mb-3">{{ detailHero.name }}</h3>
            <p class="text-white/80 italic text-base max-w-2xl mx-auto">{{ detailHero.quote }}</p>
          </div>
        </div>

        <!-- Back button -->
        <div class="mt-8 flex justify-start">
          <button
            @click="closeDetail"
            class="flex items-center gap-3 px-8 py-3 text-sm tracking-[2px] uppercase
                   bg-transparent border-2 border-yellow-600 text-yellow-600
                   hover:bg-yellow-600 hover:text-black transition-all duration-300"
          >
            <span class="text-xl leading-none">‹</span>
            <span>Back to Heroes</span>
          </button>
        </div>

      </div>


      
    </div>
  </section>
</template>

<script setup>
import { ref, computed } from "vue";
import imgA from "../assets/images/hifa.png";
import imgB from "../assets/images/yousf.png";
import rightBg from "../assets/images/Hajj_Ibrahim.PNG";
import landscapeA from "../assets/images/heroes-section1.jpg";
import landscapeB from "../assets/images/heroes-section2.jpg";

const slidesData = ref([
  [
    {
      name: "Hifaa hassn, 22",
      role: "Medical Student & Artist",
      quote: '"Even in darkness, we paint our dreams on the walls of tomorrow."',
      image: imgA,
      landscapeImage: landscapeA,
      description:
        "A keeper of memories and traditions, Nour Al-Masri combines her medical studies with artistic expression to document the resilience of Gaza.",
    },
    {
      name: "Youssef, 9",
      role: "Aspiring Football Player",
      quote: '"When I kick the ball, I forget everything. Football is my freedom."',
      image: imgB,
      landscapeImage: landscapeB,
      description:
        "Despite the challenges, Youssef dreams of becoming a professional football player, finding joy and freedom on the field.",
    },
    {
      name: "Hajj Ibrahim, 67",
      role: "Storyteller & Community Elder",
      quote: '"I have witnessed many wars, but I refuse to let war define who we are."',
      image: rightBg,
      landscapeImage: landscapeA,
      description:
        "A keeper of memories and traditions, Hajj Ibrahim gathers children under olive trees to share stories of Palestine's rich history and teaches younger generations that their identity is rooted in culture, not conflict.",
    },
  ],
]);

const currentSlide = ref(0);
const detailView = ref(false);
const detailHeroIndex = ref(0);

const getCurrentSlideHeroes = computed(() => slidesData.value[currentSlide.value]);
const allHeroes = computed(() => slidesData.value[0]);
const detailHero = computed(() => slidesData.value[0][detailHeroIndex.value]);

const openDetail = () => {
  detailHeroIndex.value = 0;
  detailView.value = true;
};

const closeDetail = () => {
  detailView.value = false;
};
</script>

<style scoped>
@keyframes fadeIn {
  from { opacity: 0; transform: translateY(16px); }
  to   { opacity: 1; transform: translateY(0); }
}
</style>