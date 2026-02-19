<template>
  <nav
    class="fixed top-0 left-0 w-full h-20 bg-gradient-to-b from-black/90 to-black/70 backdrop-blur-lg z-[1000] border-b border-gold/30"
  >
    <div
      class="max-w-[1400px] mx-auto h-full flex items-center justify-between px-6 lg:px-8"
    >
      <div>
        <h1 class="text-base md:text-lg font-normal tracking-tight text-white">
          Is Al-Ghazzawi a superhero?
        </h1>
      </div>

      <!-- Desktop Menu -->
      <ul class="hidden md:flex list-none gap-6 lg:gap-10 items-center">
        <li v-for="item in navItems" :key="item.id" class="relative">
          <a
            @click="scrollToSection(item.id)"
            :href="`#${item.id}`"
            class="transition-all duration-300 cursor-pointer"
            style="font-family: 'IBM Plex Sans', sans-serif; font-size: 13px; font-weight: 400;"
            :class="
              activeSection === item.id
                ? 'text-purple'
                : 'text-gray-300 hover:text-white'
            "
          >
            {{ item.name }}
          </a>
          <div
            v-if="activeSection === item.id"
            class="absolute -bottom-2 left-1/2 -translate-x-1/2 w-2 h-2 rounded-full bg-purple shadow-[0_0_10px_#d4af37]"
          ></div>
        </li>
      </ul>

      <!-- Mobile Hamburger Button -->
      <button
        class="md:hidden text-white focus:outline-none z-50"
        @click="toggleMenu"
        aria-label="Toggle menu"
      >
        <div class="w-6 h-5 relative flex flex-col justify-between">
          <span
            class="w-full h-0.5 bg-white transition-all duration-300"
            :class="{ 'rotate-45 translate-y-2.5': isMenuOpen }"
          ></span>
          <span
            class="w-full h-0.5 bg-white transition-all duration-300"
            :class="{ 'opacity-0': isMenuOpen }"
          ></span>
          <span
            class="w-full h-0.5 bg-white transition-all duration-300"
            :class="{ '-rotate-45 -translate-y-2': isMenuOpen }"
          ></span>
        </div>
      </button>

      <!-- Mobile Menu Overlay -->
      <div
        class="fixed inset-0 bg-black/95 backdrop-blur-xl z-40 transition-transform duration-300 md:hidden flex flex-col items-center justify-center"
        :class="isMenuOpen ? 'translate-x-0' : 'translate-x-full'"
      >
        <ul class="flex flex-col gap-8 text-center">
          <li v-for="item in navItems" :key="item.id">
            <a
              @click="scrollToSection(item.id)"
              :href="`#${item.id}`"
              class="text-xl font-medium tracking-[2px] uppercase transition-all duration-300 cursor-pointer block py-2"
              :class="
                activeSection === item.id
                  ? 'text-purple'
                  : 'text-gray-300 hover:text-white'
              "
            >
              {{ item.name }}
            </a>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<script setup>
import { ref } from "vue";

defineProps({
  activeSection: {
    type: String,
    default: "intro",
  },
});

const emit = defineEmits(["navigate"]);

const navItems = [
  { id: "intro", name: "INTRO" },
  { id: "story", name: "THE STORY" },
  { id: "heroes", name: "HEROES" },
  { id: "film", name: "THE FILM" },
  { id: "team", name: "TEAM" },
];

const isMenuOpen = ref(false);

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value;
};

const scrollToSection = (sectionId) => {
  isMenuOpen.value = false;
  emit("navigate", sectionId);
};
</script>
