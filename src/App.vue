<template>
  <div class="app">
    <Navbar
      :activeSection="activeSection"
      :currentSectionIndex="currentSectionIndex"
      :totalSections="sections.length"
      @navigate="navigateToSection"
    />

    <!-- Desktop navigation arrows -->
    <button
      v-if="currentSectionIndex > 0"
      @click="scrollToIndex(currentSectionIndex - 1)"
      class="hidden md:flex fixed left-4 top-1/2 -translate-y-1/2 z-50 w-9 h-9 items-center justify-center border border-white/15 bg-black/40 backdrop-blur-sm text-white/40 hover:text-white/80 hover:border-white/40 transition-all duration-300 cursor-pointer rounded-full"
      aria-label="Previous section"
    >
      <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round">
        <path d="M15 18l-6-6 6-6"/>
      </svg>
    </button>
    <button
      v-if="currentSectionIndex < sections.length - 1"
      @click="scrollToIndex(currentSectionIndex + 1)"
      class="hidden md:flex fixed right-4 top-1/2 -translate-y-1/2 z-50 w-9 h-9 items-center justify-center border border-white/15 bg-black/40 backdrop-blur-sm text-white/40 hover:text-white/80 hover:border-white/40 transition-all duration-300 cursor-pointer rounded-full"
      aria-label="Next section"
    >
      <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round">
        <path d="M9 18l6-6-6-6"/>
      </svg>
    </button>

    <div class="scroll-wrapper" @wheel="handleScroll" ref="scrollWrapper">
      <div class="sections-container" ref="sectionsContainer">
        <IntroSection id="intro" />
        <div class="section-divider"></div>
        <StorySection id="story" />
        <div class="section-divider"></div>
        <HeroesSection id="heroes" />
        <div class="section-divider"></div>
        <FilmSection id="film" />
        <div class="section-divider"></div>
        <TeamSection id="team" />
      </div>
    </div>
  </div>
</template>

<script setup>
import Navbar from "./components/Navbar.vue";
import IntroSection from "./components/IntroSection.vue";
import StorySection from "./components/StorySection.vue";
import HeroesSection from "./components/HeroesSection.vue";
import FilmSection from "./components/FilmSection.vue";
import TeamSection from "./components/TeamSection.vue";
import { onMounted, ref, onBeforeUnmount } from "vue";

const sectionsContainer = ref(null);
const sections = ["intro", "story", "heroes", "film", "team"];
const currentSectionIndex = ref(0);
const activeSection = ref(sections[0]);
const isScrolling = ref(false);

const isMobile = () => window.innerWidth < 768;

onMounted(() => {
  activeSection.value = sections[0];
  handleResize();
  window.addEventListener("resize", handleResize);
  window.addEventListener("scroll", handleNativeScroll);
});

onBeforeUnmount(() => {
  window.removeEventListener("resize", handleResize);
  window.removeEventListener("scroll", handleNativeScroll);
});

function handleNativeScroll() {
  if (!isMobile()) return;
}

function handleScroll(event) {
  if (isMobile()) return;
  event.preventDefault();
  if (isScrolling.value) return;

  const delta = event.deltaY || event.deltaX || 0;
  if (Math.abs(delta) < 30) return;

  const direction = delta > 0 ? 1 : -1;
  const newIndex = currentSectionIndex.value + direction;

  if (newIndex < 0 || newIndex >= sections.length) return;
  scrollToIndex(newIndex);
}

function navigateToSection(sectionId) {
  if (isMobile()) {
    const element = document.getElementById(sectionId);
    if (element) {
      element.scrollIntoView({ behavior: "smooth" });
      activeSection.value = sectionId;
    }
    return;
  }
  const sectionIndex = sections.indexOf(sectionId);
  if (sectionIndex === -1) return;
  scrollToIndex(sectionIndex);
}

function scrollToIndex(index) {
  isScrolling.value = true;
  currentSectionIndex.value = index;
  activeSection.value = sections[index];

  const container = sectionsContainer.value;
  const scrollPosition = index * window.innerWidth;
  if (container) container.style.transform = `translateX(-${scrollPosition}px)`;

  setTimeout(() => {
    isScrolling.value = false;
  }, 900);
}

function handleResize() {
  const container = sectionsContainer.value;
  if (!container) return;

  if (isMobile()) {
    container.style.transform = "none";
  } else {
    const scrollPosition = currentSectionIndex.value * window.innerWidth;
    container.style.transform = `translateX(-${scrollPosition}px)`;
  }
}
</script>

<style scoped>
.app {
  width: 100%;
  height: 100vh;
  overflow-y: auto;
  overflow-x: hidden;
  background: #000;
}

@media (min-width: 768px) {
  .app {
    overflow: hidden;
  }
}

.scroll-wrapper {
  width: 100%;
  height: auto;
  min-height: 100vh;
  position: relative;
}

@media (min-width: 768px) {
  .scroll-wrapper {
    height: 100vh;
    overflow: hidden;
  }
}

.sections-container {
  display: flex;
  flex-direction: column;
  width: 100%;
  height: auto;
  transition: transform 0.9s cubic-bezier(0.65, 0, 0.35, 1);
  will-change: transform;
}

@media (min-width: 768px) {
  .sections-container {
    flex-direction: row;
    height: 100vh;
    width: auto;
  }
}

.sections-container > *:not(.section-divider) {
  width: 100%;
  min-height: 100vh;
  flex-shrink: 0;
}

@media (min-width: 768px) {
  .sections-container > *:not(.section-divider) {
    min-width: 100vw;
    width: 100vw;
    height: 100vh;
  }
}

/* Mobile divider */
.section-divider {
  flex-shrink: 0;
  display: block;
  width: auto;
  height: 1px;
  background-color: transparent;
  margin-top: 36px;
  margin-bottom: 36px;
  margin-left: 32px;
  margin-right: 32px;
  border: none;
  border-top: 3px solid #251B02;
}

@media (min-width: 768px) {
  .section-divider {
    display: none;
  }
}
</style>
