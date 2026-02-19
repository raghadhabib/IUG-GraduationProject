<template>
  <div class="app">
    <Navbar :activeSection="activeSection" @navigate="navigateToSection" />

    <div class="scroll-wrapper" @wheel="handleScroll" ref="scrollWrapper">
      <div class="sections-container" ref="sectionsContainer">
        <IntroSection id="intro" />
        <StorySection id="story" />
        <HeroesSection id="heroes" />
        <FilmSection id="film" />
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
const activeSection = ref(sections[currentSectionIndex.value]);
const isScrolling = ref(false);

const isMobile = () => window.innerWidth < 768;

onMounted(() => {
  activeSection.value = sections[currentSectionIndex.value] || "intro";
  // Initial position set
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
  
  // Simple active section detection based on scroll position could go here
  // For now, let's just stick to letting the user scroll naturally
}

function handleScroll(event) {
  // If mobile, let native scroll handle it
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
    // Reset transform on mobile so vertical layout works
    container.style.transform = "none";
  } else {
    // Restore horizontal position on desktop
    const scrollPosition = currentSectionIndex.value * window.innerWidth;
    container.style.transform = `translateX(-${scrollPosition}px)`;
  }
}
</script>

<style scoped>
.app {
  width: 100%;
  height: 100vh;
  /* Unlock overflow on mobile so strict vertical scrolling works */
  overflow-y: auto;
  overflow-x: hidden;
  background: #000;
}

/* Ensure horizontal scroll lock only applies to desktop */
@media (min-width: 768px) {
  .app {
    overflow: hidden;
  }
}

.scroll-wrapper {
  width: 100%;
  /* Height auto on mobile to allow scrolling */
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
  /* Column on mobile */
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
    width: auto; /* Allow it to grow horizontally */
  }
}

.sections-container > * {
  width: 100%;
  min-height: 100vh;
  flex-shrink: 0;
}

@media (min-width: 768px) {
  .sections-container > * {
    min-width: 100vw;
    width: 100vw;
    height: 100vh;
  }
}
</style>
