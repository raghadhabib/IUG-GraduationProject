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
        <!-- Desktop Slider (Hidden on Mobile) -->
        <div class="hidden md:block">
          <div
            class="grid grid-cols-1 lg:grid-cols-3 gap-8 items-start mt-12 transition-all duration-700 ease-in-out"
          >
            <div class="grid grid-cols-1 md:grid-cols-2 lg:col-span-2 gap-6">
              <!-- Card 1 -->
              <div
                class="relative bg-black overflow-hidden transition-all duration-700 ease-in-out"
              >
                <div class="relative w-full h-96 overflow-hidden">
                  <img
                    :src="getCurrentSlideHeroes[0].image"
                    :alt="getCurrentSlideHeroes[0].name"
                    class="w-full h-full object-cover object-top transition-transform duration-300 ease-in-out hover:scale-105"
                  />
                  <div
                    class="absolute bottom-0 left-0 right-0 bg-linear-to-t from-black/90 via-black/70 to-black/30 p-6 pb-7"
                  >
                    <div class="text-white">
                      <p
                        class="text-yellow-600 text-xs uppercase tracking-wider mb-2 font-medium"
                      >
                        {{ getCurrentSlideHeroes[0].role }}
                      </p>
                      <h3 class="text-2xl font-light mb-3 leading-tight">
                        {{ getCurrentSlideHeroes[0].name }}
                      </h3>
                      <p class="text-white/80 italic text-sm leading-relaxed">
                        {{ getCurrentSlideHeroes[0].quote }}
                      </p>
                    </div>
                  </div>
                </div>
              </div>

              <!-- Card 2 -->
              <div
                class="relative bg-black overflow-hidden transition-all duration-700 ease-in-out"
              >
                <div class="relative w-full h-96 overflow-hidden">
                  <img
                    :src="getCurrentSlideHeroes[1].image"
                    :alt="getCurrentSlideHeroes[1].name"
                    class="w-full h-full object-cover transition-transform duration-300 ease-in-out hover:scale-105"
                  />
                  <div
                    class="absolute bottom-0 left-0 right-0 bg-linear-to-t from-black/90 via-black/70 to-black/30 p-6 pb-7"
                  >
                    <div class="text-white">
                      <p
                        class="text-yellow-600 text-xs uppercase tracking-wider mb-2 font-medium"
                      >
                        {{ getCurrentSlideHeroes[1].role }}
                      </p>
                      <h3 class="text-2xl font-light mb-3 leading-tight">
                        {{ getCurrentSlideHeroes[1].name }}
                      </h3>
                      <p class="text-white/80 italic text-sm leading-relaxed">
                        {{ getCurrentSlideHeroes[1].quote }}
                      </p>
                    </div>
                  </div>
                </div>
              </div>
            </div>

            <!-- Right side: Large featured hero -->
            <div class="relative">
              <div
                class="relative flex items-end overflow-hidden bg-black transition-all duration-700 ease-in-out"
              >
                <div
                  class="absolute inset-0 bg-cover bg-center transition-transform duration-300 ease-in-out hover:scale-102"
                  :style="{
                    backgroundImage: `url(${getCurrentSlideHeroes[2].image})`,
                  }"
                ></div>
                <div
                  class="absolute inset-0 bg-gradient-to-t from-black/85 via-black/60 to-black/20"
                ></div>

            <div class="relative z-10 p-9 text-white w-full h-full flex flex-col justify-end group">
                <p
                  class="text-yellow-600 text-xs uppercase tracking-wider mb-2 font-medium"
                >
                  {{ getCurrentSlideHeroes[2].role }}
                </p>
                <h3 class="text-4xl font-light mb-4 leading-tight">
                  {{ getCurrentSlideHeroes[2].name }}
                </h3>
                
                <div class="max-h-0 opacity-0 group-hover:max-h-[500px] group-hover:opacity-100 transition-all duration-500 ease-in-out overflow-hidden">
                  <p class="text-white/90 text-base leading-relaxed mb-4">
                    {{ getCurrentSlideHeroes[2].description }}
                  </p>
                  <blockquote
                    class="border-l-2 border-yellow-600/80 pl-4 text-white/90 italic text-base leading-relaxed mb-5"
                  >
                    {{ getCurrentSlideHeroes[2].quote }}
                  </blockquote>
                  <button
                    class="bg-transparent border border-yellow-600/90 text-yellow-600/90 px-5 py-2.5 text-xs uppercase tracking-wider font-medium transition-all duration-300 hover:bg-yellow-600/90 hover:text-black"
                  >
                    READ MORE
                  </button>
                </div>
              </div>
              </div>
            </div>
          </div>

           <!-- Navigation arrows for the entire slider -->
          <button
            class="absolute top-1/2 -left-7 transform -translate-y-1/2 z-20 bg-black/70 hover:bg-black/90 border-0 text-white w-14 h-14 rounded-full text-2xl cursor-pointer flex items-center justify-center transition-all duration-300 hover:scale-110"
            @click="prevSlide"
            aria-label="Previous slide"
          >
            ‹
          </button>
          <button
            class="absolute top-1/2 -right-7 transform -translate-y-1/2 z-20 bg-black/70 hover:bg-black/90 border-0 text-white w-14 h-14 rounded-full text-2xl cursor-pointer flex items-center justify-center transition-all duration-300 hover:scale-110"
            @click="nextSlide"
            aria-label="Next slide"
          >
            ›
          </button>
        </div>

        <!-- Mobile Vertical List (Visible on Mobile) -->
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
                <h3 class="text-3xl font-light text-white mb-2">
                  {{ hero.name }}
                </h3>
                <p class="text-white/80 italic text-sm leading-relaxed line-clamp-3">
                  {{ hero.quote }}
                </p>
                
                 <div class="mt-4 pt-4 border-t border-white/10" v-if="hero.description">
                   <p class="text-white/70 text-sm line-clamp-3">
                     {{ hero.description }}
                   </p>
                 </div>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- Bottom navigation dots -->
      <div class="mt-10 flex justify-center items-center">
        <div class="text-white/50 text-xs uppercase tracking-wider">
          The Album
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

// Create slides data - each slide contains 3 heroes
const slidesData = ref([
  [
    {
      name: "Hifaa hassn, 22",
      role: "Medical Student & Artist",
      quote:
        '"Even in darkness, we paint our dreams on the walls of tomorrow."',
      image: imgA,
      description:
        "A keeper of memories and traditions, Nour Al-Masri combines her medical studies with artistic expression to document the resilience of Gaza.",
    },
    {
      name: "Youssef, 9",
      role: "Aspiring Football Player",
      quote:
        '"When I kick the ball, I forget everything. Football is my freedom."',
      image: imgB,
      description:
        "Despite the challenges, Youssef dreams of becoming a professional football player, finding joy and freedom on the field.",
    },
    {
      name: "Hajj Ibrahim, 67",
      role: "Storyteller & Community Elder",
      quote:
        '"I have witnessed many wars, but I refuse to let war define who we are."',
      image: rightBg,
      description:
        "A keeper of memories and traditions, Hajj Ibrahim gathers children under olive trees to share stories of Palestine's rich history. Having lived through decades of conflict, he remains a pillar of wisdom and peace, teaching younger generations that their identity is rooted in culture, not conflict.",
    },
  ],
]);

const currentSlide = ref(0);

const getCurrentSlideHeroes = computed(() => {
  return slidesData.value[currentSlide.value];
});

const allHeroes = computed(() => {
  return slidesData.value[0];
});

const prevSlide = () => {
  currentSlide.value =
    (currentSlide.value - 1 + slidesData.value.length) %
    slidesData.value.length;
};

const nextSlide = () => {
  currentSlide.value = (currentSlide.value + 1) % slidesData.value.length;
};
</script>

<style scoped>
/* Custom scoped styles if needed */
</style>
