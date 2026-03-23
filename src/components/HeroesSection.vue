<template>
  <section
    class="relative md:pt-20 w-full h-full flex justify-center overflow-hidden bg-black"
    :class="detailView ? 'items-start' : 'items-center'"
  >
    <div
      class="relative z-10 max-w-350 w-[90%] px-8 mx-auto"
      :class="detailView ? 'py-8' : 'py-10'"
    >
      <h2 class="text-6xl lg:text-5xl md:text-4xl font-normal text-white mb-4">
        The Heroes
      </h2>
      <p class="text-xl md:text-lg text-white/70 mb-2 font-normal max-w-200">
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
            class="group relative bg-black overflow-hidden"
          >
            <div class="relative w-full h-[380px] overflow-hidden">
              <img
                :src="hero.image"
                :alt="hero.name"
                class="w-full h-full object-top duration-500 ease-in-out object-cover"
              />
              <div class="vignette"></div>
              <div
                class="absolute inset-0 bg-gradient-to-t from-black/95 via-black/60 to-black/10 transition-all duration-500 group-hover:from-black group-hover:via-black/90 group-hover:to-black/70"
              ></div>
              <div class="absolute bottom-0 left-0 right-0 p-6 pb-7 text-white">
                <p
                  class="text-yellow-600 text-xs uppercase tracking-wider mb-2 font-medium"
                >
                  {{ hero.role }}
                </p>
                <h3 class="text-2xl font-light leading-tight">
                  {{ hero.name }}
                </h3>
                <div
                  class="max-h-0 opacity-0 group-hover:max-h-40 group-hover:opacity-100 overflow-hidden transition-all duration-500 ease-in-out mb-0 group-hover:mb-3 rounded px-3 py-2"
                >
                  <p class="text-white/85 text-sm leading-relaxed">
                    {{ hero.description }}
                  </p>
                </div>
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

        <!-- Mobile: cards list -->
        <div class="md:hidden flex flex-col gap-8 mt-8">
          <div v-for="(hero, index) in allHeroes" :key="index" class="relative">
            <div class="relative w-full h-[400px] overflow-hidden rounded-lg">
              <img
                :src="hero.image"
                :alt="hero.name"
                class="w-full h-full object-cover"
              />
              <div class="vignette"></div>
              <div
                class="absolute inset-0 bg-gradient-to-t from-black via-black/90 to-black/70"
              ></div>
              <div class="absolute bottom-0 left-0 right-0 p-6 text-white">
                <p
                  class="text-yellow-600 text-xs uppercase tracking-wider mb-2 font-medium"
                >
                  {{ hero.role }}
                </p>
                <h3 class="text-2xl font-light leading-tight mb-3">
                  {{ hero.name }}
                </h3>
                <!-- description hidden on mobile -->
                <div class="hidden">
                  <p class="text-white/85 text-sm leading-relaxed">
                    {{ hero.description }}
                  </p>
                </div>
                <div class="border-l-2 border-yellow-600 pl-3">
                  <p class="text-white/75 italic text-sm leading-relaxed">
                    {{ hero.quote }}
                  </p>
                </div>
              </div>
            </div>
          </div>

          <!-- Mobile: +2.51M image shown inline after cards when expanded -->
          <div
            v-if="mobileDetailOpen"
            class="relative w-full animate-[fadeIn_0.6s_ease-out]"
          >
            <div class="relative w-full h-[55vh] overflow-hidden rounded-lg">
              <img
                src="../assets/images/heroDetails.webp"
                alt="+2.51 Million Ghazzawi"
                class="w-full h-full object-cover object-center"
              />
              <div class="vignette"></div>
              <div
                class="absolute inset-0 bg-gradient-to-t from-black/90 via-black/30 to-transparent"
              ></div>
              <div
                class="absolute bottom-0 left-0 right-0 pb-8 px-6 text-white"
              >
                <h3 class="text-3xl font-light mb-3">+2.51 Million Ghazzawi</h3>
                <p class="text-sm text-white/80 leading-relaxed">
                  From all the people of Gaza — of all ages, circumstances, and
                  conditions — what was shown is just a glimpse, a single
                  example.
                </p>
              </div>
            </div>
          </div>
        </div>

        <!-- View More / View Less button -->
        <div class="flex justify-end mb-4 mt-6">
          <!-- Desktop button -->
          <button
            class="hidden md:block relative px-10 py-3.5 text-sm tracking-[2px] uppercase border-2 border-gold bg-gold text-white transition-all duration-300 overflow-hidden group cursor-pointer"
            @click="openDetail"
          >
            <span
              class="absolute inset-0 bg-gold -translate-x-full group-hover:translate-x-0 transition-transform duration-300 -z-10"
            ></span>
            <span class="relative transition-colors duration-300"
              >VIEW MORE</span
            >
          </button>

          <!-- Mobile button toggles inline detail -->
          <button
            class="md:hidden relative px-10 py-3.5 text-sm tracking-[2px] uppercase border-2 border-gold bg-gold text-white transition-all duration-300 overflow-hidden group cursor-pointer"
            @click="mobileDetailOpen = !mobileDetailOpen"
          >
            <span
              class="absolute inset-0 bg-gold -translate-x-full group-hover:translate-x-0 transition-transform duration-300 -z-10"
            ></span>
            <span class="relative transition-colors duration-300">
              {{ mobileDetailOpen ? "VIEW LESS" : "VIEW MORE" }}
            </span>
          </button>
        </div>
      </div>

      <!-- ─── DETAIL VIEW (desktop only) ─── -->
      <div v-else class="mt-8 animate-[fadeIn_0.6s_ease-out]">
        <div class="relative w-full rounded-sm" style="overflow: visible">
          <div class="relative w-full h-[55vh] overflow-hidden">
            <img
              src="../assets/images/heroDetails.webp"
              :alt="detailHero.name"
              class="w-full h-full object-cover object-center"
            />
            <div class="vignette"></div>
            <div
              class="absolute inset-0 bg-gradient-to-t from-black/90 via-black/30 to-transparent"
            ></div>
            <div
              class="absolute bottom-0 left-0 right-0 pb-8 px-8 text-start text-white"
            >
              <h3 class="text-5xl lg:text-6xl md:text-4xl font-light mb-3">
                +2.51 Million Ghazzawi
              </h3>
              <p class="text-sm sm:text-2xl text-white/80 text-start">
                From all the people of Gaza — of all ages, circumstances, and
                conditions — what was shown is just a glimpse, a single example.
              </p>
            </div>
          </div>
          <div class="flex justify-end">
            <button
              @click="closeDetail"
              class="relative px-10 py-3.5 text-sm tracking-[2px] uppercase border-2 border-gold bg-gold text-white transition-all duration-300 overflow-hidden group cursor-pointer"
            >
              <span
                class="absolute inset-0 bg-gold -translate-x-full group-hover:translate-x-0 transition-transform duration-300 -z-10"
              ></span>
              <span class="relative">VIEW LESS</span>
            </button>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, computed } from "vue";
import imgA from "../assets/images/hifa.webp";
import imgB from "../assets/images/yousf.webp";
import rightBg from "../assets/images/Hajj_Ibrahim.webp";

const slidesData = ref([
  [
    {
      name: "Yosuf hassn, 15",
      role: "Karate Player",
      quote:
        '" I love karate, and my soul is deeply connected to it. All my sorrow for Gaza, I used to release through karate. "',
      image: imgB,
      description:
        "A black-belt athlete and four-time national champion. After qualifying for the national team just before the conflict, Youssef continued training in open fields and displacement camps. He maintains his athletic discipline despite the loss of all professional facilities.",
    },
    {
      name: "Hifaa Bassam, 22",
      role: "Cellist & UX/UI Designer",
      quote:
        '"From the very first moment I played again, I felt like I found myself once more."',
      image: imgA,
      description:
        "An IT Engineering graduate and professional cellist. After recovering her instrument from her damaged home, Haifaa resumed playing as a form of cultural resilience. She balances her career as a digital designer with her commitment to music.",
    },
    {
      name: "Kamal Al-Hajj, 73",
      role: "Religious scholar & calligrapher",
      quote:
        '"I love life, I love Gaza; I feel it is a great opportunity for more good deeds and greater happiness in the hereafter."',
      image: rightBg,
      description:
        "A religious man, calligrapher, and artist who lost his home and son in the war. Despite the pain, he remains reflective and hopeful, viewing life as a path to good deeds and eternal happiness in the afterlife.",
    },
  ],
]);

const currentSlide = ref(0);
const detailView = ref(false); // desktop full-page detail
const mobileDetailOpen = ref(false); // mobile inline detail
const detailHeroIndex = ref(0);

const getCurrentSlideHeroes = computed(
  () => slidesData.value[currentSlide.value]
);
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
  from {
    opacity: 0;
    transform: translateY(16px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.vignette {
  position: absolute;
  inset: 0;
  pointer-events: none;
  z-index: 1;
  background: radial-gradient(
    ellipse at center,
    transparent 40%,
    rgba(0, 0, 0, 0.55) 75%,
    rgba(0, 0, 0, 0.85) 100%
  );
}
</style>
