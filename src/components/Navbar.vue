<template>
  <nav class="navbar fixed top-0 left-0 w-full z-[1000]">
    <!-- Main navbar content -->
    <div class="w-full h-20 bg-black/80 backdrop-blur-lg">
      <div class="max-w-[1400px] mx-auto h-full flex items-center justify-between px-6 lg:px-8">
        <div>
          <h1 class="text-base md:text-lg font-normal tracking-tight text-white">
            Is Al-Ghazzawi a superhero?
          </h1>
        </div>

        <!-- Desktop Menu -->
        <ul class="hidden md:flex list-none gap-6 lg:gap-10 items-center">
          <li v-for="item in navItems" :key="item.id" class="relative">
            <a
              @click.prevent="scrollToSection(item.id)"
              href="#"
              class="transition-all duration-300 cursor-pointer bg-black backdrop-blur-sm"
              style="font-family: 'IBM Plex Sans', sans-serif; font-size: 13px; font-weight: 400;"
              :style="activeSection === item.id ? { color: item.color } : {}"
              :class="activeSection === item.id ? '' : 'text-gray-300'"
            >
              {{ item.name }}
            </a>
            <div
              v-if="activeSection === item.id"
              class="absolute -bottom-2 left-1/2 -translate-x-1/2 w-2 h-2 rounded-full"
              :style="{ backgroundColor: item.color, boxShadow: `0 0 10px ${item.color}` }"
            ></div>
          </li>
        </ul>

        <!-- Mobile Hamburger -->
        <button
          class="cursor-pointer md:hidden text-white focus:outline-none z-50"
          @click="toggleMenu"
          aria-label="Toggle menu"
        >
          <div class="w-6 h-5 relative flex flex-col justify-between">
            <span class="w-full h-0.5 bg-white transition-all duration-300" :class="{ 'rotate-45 translate-y-2.5': isMenuOpen }"></span>
            <span class="w-full h-0.5 bg-white transition-all duration-300" :class="{ 'opacity-0': isMenuOpen }"></span>
            <span class="w-full h-0.5 bg-white transition-all duration-300" :class="{ '-rotate-45 -translate-y-2': isMenuOpen }"></span>
          </div>
        </button>

        <!-- Mobile Menu Overlay -->
        <div
  v-if="isMenuOpen"
  class="fixed top-0 left-0 w-screen md:hidden flex flex-col items-center"
  style="background-color: rgba(0,0,0,0.9); backdrop-filter: blur(10px); z-index: 999;"
>
  <!-- Close button -->
  <button
    @click="toggleMenu"
    class="cursor-pointer self-end px-6 py-4 text-white text-2xl"
    aria-label="Close menu"
  >
    ✕
  </button>

  <ul class="flex flex-col gap-6 w-full px-8 py-5 text-center">
    <li v-for="item in navItems" :key="item.id">
      <a
      
        @click.prevent="scrollToSection(item.id)"
        href="#"
        class="text-lg font-medium tracking-[2px] uppercase transition-all duration-300 cursor-pointer block py-2"
        :style="activeSection === item.id ? { color: item.color } : {}"
        :class="activeSection === item.id ? '' : 'text-gray-300 hover:text-white'"
      >
        {{ item.name }}
      </a>
    </li>
  </ul>
</div>
      </div>
    </div>

    <!-- Merged gradient progress line -->
    <div class="relative w-full h-[1.5px]">
      <!-- Dim full track always visible -->
      <div
        class="absolute inset-0 opacity-5"
        style="background: linear-gradient(to right, #9333EA, #EF4444, #10B981, #3B82F6, #F97316);"
      ></div>
      <!-- Bright fill that grows with progress -->
      <div
        class="absolute top-0 left-0 h-full transition-all duration-700 ease-out"
        :style="{
          width: progressWidth,
          background: 'linear-gradient(to right, #9333EA, #EF4444, #10B981, #3B82F6, #F97316)'
        }"
      ></div>
    </div>
  </nav>
</template>

<script setup>
import { ref, computed } from "vue";

const props = defineProps({
  activeSection: {
    type: String,
    default: "intro",
  },
  currentSectionIndex: {
    type: Number,
    default: 0,
  },
  totalSections: {
    type: Number,
    default: 5,
  },
});

const emit = defineEmits(["navigate"]);

const navItems = [
  { id: "intro",  name: "INTRO",      color: "#9333EA" },
  { id: "story",  name: "THE STORY",  color: "#EF4444" },
  { id: "heroes", name: "THE HEROES", color: "#10B981" },
  { id: "film",   name: "THE FILM",   color: "#3B82F6" },
  { id: "team",   name: "THE TEAM",   color: "#F97316" },
];

const isMenuOpen = ref(false);

const progressWidth = computed(() => {
  const percent = (props.currentSectionIndex / (props.totalSections - 1)) * 100;
  return `${percent}%`;
});

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value;
};

const scrollToSection = (sectionId) => {
  isMenuOpen.value = false;
  emit("navigate", sectionId);
};
</script>

<style scoped>
.navbar {
  border-bottom: none;
}
</style>