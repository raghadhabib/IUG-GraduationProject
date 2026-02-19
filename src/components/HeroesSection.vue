<template>
  <section
    class="relative pt-20 w-full h-full flex items-start justify-center overflow-hidden bg-black"
  >
    <div class="relative z-10 max-w-350 w-[90%] px-8 py-24 md:py-16 mx-auto">
      <h2 class="text-6xl lg:text-5xl md:text-4xl font-normal text-white mb-4">
        The Heroes
      </h2>
      <p class="text-xl md:text-lg text-white/70 mb-2 font-normal max-w-165">
        Meet the extraordinary individuals whose courage and resilience
        illuminate the true spirit of Gaza.
      </p>

      <div class="relative">
        <!-- Desktop: 3 equal cards -->
        <div class="hidden md:grid grid-cols-3 gap-6 mt-12">
          <div
            v-for="(hero, index) in getCurrentSlideHeroes"
            :key="index"
            class="group relative bg-black overflow-hidden cursor-pointer"
          >
            <div class="relative w-full h-[380px] overflow-hidden">
              <!-- Image -->
              <img
                :src="hero.image"
                :alt="hero.name"
                class="w-full h-full object-cover object-top transition-transform duration-500 ease-in-out group-hover:scale-105"
              />

              <!-- Gradient overlay — deepens on hover -->
              <div
                class="absolute inset-0 bg-gradient-to-t from-black/95 via-black/60 to-black/10 transition-all duration-500 group-hover:from-black/95 group-hover:via-black/75 group-hover:to-black/30"
              ></div>

              <!-- Card content -->
              <div class="absolute bottom-0 left-0 right-0 p-6 pb-7 text-white">
                <!-- Role -->
                <p class="text-yellow-600 text-xs uppercase tracking-wider mb-2 font-medium">
                  {{ hero.role }}
                </p>

                <!-- Name -->
                <h3 class="text-2xl font-light mb-3 leading-tight">
                  {{ hero.name }}
                </h3>

                <!-- Description — hidden by default, slides in on hover -->
                <div
                  class="max-h-0 opacity-0 group-hover:max-h-40 group-hover:opacity-100 overflow-hidden transition-all duration-500 ease-in-out mb-0 group-hover:mb-3"
                >
                  <p class="text-white/85 text-sm leading-relaxed">
                    {{ hero.description }}
                  </p>
                </div>

                <!-- Quote — always visible but gets gold border on hover -->
                <div
                  class="transition-all duration-300 group-hover:border-l-2 group-hover:border-yellow-600 group-hover:pl-3"
                >
                  <p class="text-white/75 italic text-sm leading-relaxed">
                    {{ hero.quote }}
                  </p>
                </div>
              </div>
            </div>
          </div>
        </div>

        <!-- Navigation arrows -->
        <button
          class="hidden md:flex absolute top-1/2 -left-7 transform -translate-y-1/2 z-20 bg-black/70 hover:bg-black/90 border-0 text-white w-14 h-14 rounded-full text-2xl cursor-pointer items-center justify-center transition-all duration-300 hover:scale-110"
          @click="prevSlide"
          aria-label="Previous slide"
        >
          ‹
        </button>
        <button
          class="hidden md:flex absolute top-1/2 -right-7 transform -translate-y-1/2 z-20 bg-black/70 hover:bg-black/90 border-0 text-white w-14 h-14 rounded-full text-2xl cursor-pointer items-center justify-center transition-all duration-300 hover:scale-110"
          @click="nextSlide"
          aria-label="Next slide"
        >
          ›
        </button>

        <!-- Mobile Vertical List -->
        <div class="md:hidden flex flex-col gap-8 mt-8">
          <div v-for="(hero, index) in allHeroes" :key="index" class="relative group">
            <div class="relative w-full h-[400px] overflow-hidden rounded-lg">
              <img
                :src="hero.image"
                :alt="hero.name"
                class="w-full h-full object-cover transition-transform duration-500 ease-in-out group-hover:scale-105"
              />
              <div class="absolute inset-0 bg-gradient-to-t from-black/90 via-black/60 to-transparent"></div>
              <div class="absolute bottom-0 left-0 right-0 p-6">
                <p class="text-yellow-600 text-xs uppercase tracking-wider mb-2 font-medium">
                  {{ hero.role }}
                </p>
                <h3 class="text-3xl font-light text-white mb-2">{{ hero.name }}</h3>
                <p class="text-white/80 italic text-sm leading-relaxed">{{ hero.quote }}</p>
                <div class="mt-4 pt-4 border-t border-white/10" v-if="hero.description">
                  <p class="text-white/70 text-sm line-clamp-3">{{ hero.description }}</p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- Bottom label -->
      <div class="mt-10 flex justify-center items-center">
        <div class="text-white/50 text-xs uppercase tracking-wider">The Album</div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, computed } from "vue";
import imgA from "../assets/images/hifa.png";
import imgB from "../assets/images/yousf.png";
import rightBg from "../assets/images/Hajj_Ibrahim.PNG";

const slidesData = ref([
  [
    {
      name: "Hifaa hassn, 22",
      role: "Medical Student & Artist",
      quote: '"Even in darkness, we paint our dreams on the walls of tomorrow."',
      image: imgA,
      description:
        "A keeper of memories and traditions, Nour Al-Masri combines her medical studies with artistic expression to document the resilience of Gaza.",
    },
    {
      name: "Youssef, 9",
      role: "Aspiring Football Player",
      quote: '"When I kick the ball, I forget everything. Football is my freedom."',
      image: imgB,
      description:
        "Despite the challenges, Youssef dreams of becoming a professional football player, finding joy and freedom on the field.",
    },
    {
      name: "Hajj Ibrahim, 67",
      role: "Storyteller & Community Elder",
      quote: '"I have witnessed many wars, but I refuse to let war define who we are."',
      image: rightBg,
      description:
        "A keeper of memories and traditions, Hajj Ibrahim gathers children under olive trees to share stories of Palestine's rich history and teaches younger generations that their identity is rooted in culture, not conflict.",
    },
  ],
]);

const currentSlide = ref(0);

const getCurrentSlideHeroes = computed(() => slidesData.value[currentSlide.value]);
const allHeroes = computed(() => slidesData.value[0]);

const prevSlide = () => {
  currentSlide.value = (currentSlide.value - 1 + slidesData.value.length) % slidesData.value.length;
};
const nextSlide = () => {
  currentSlide.value = (currentSlide.value + 1) % slidesData.value.length;
};
</script>