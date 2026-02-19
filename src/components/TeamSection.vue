<template>
  <section class="relative pt-20 w-full h-full overflow-hidden bg-black">
    <div class="relative z-10 max-w-1400 w-[90%] mx-auto px-8 pt-8">
      <!-- Header -->
      <div class="mb-12 max-w-275">
        <!-- replaced .team-title with Tailwind utilities -->
        <h2
          class="font-serif text-[60px] leading-[0.95] text-white font-normal -tracking-[1px] drop-shadow-[0_10px_30px_rgba(0,0,0,0.6)] mb-4"
        >
          The Team
        </h2>
        <p class="text-white/65 text-base max-w-[900px]">
          The visionaries and artists who brought this story to life.
        </p>
      </div>

      <!-- Team grid -->
      <div
        class="team-grid grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-10"
      >
        <article
          v-for="(member, idx) in team"
          :key="idx"
          class="group overflow-hidden rounded-md bg-[rgba(255,255,255,0.02)] border border-[rgba(212,175,55,0.06)] transform transition-transform duration-300 will-change-transform hover:-translate-y-2.5 hover:shadow-2xl"
        >
          <!-- keep Tailwind width/height -->
          <div
            class="relative w-[272px] h-[294px] overflow-hidden mx-auto bg-[#111]"
          >
            <img
              :src="member.image"
              :alt="member.name"
              class="w-full h-full object-cover block transition-transform duration-300 ease-in-out origin-center group-hover:scale-105"
            />
            <!-- overlay using Tailwind -->
            <div
              class="absolute inset-0 bg-gradient-to-b from-transparent via-black/30 to-black/75 pointer-events-none"
            ></div>
          </div>

          <div class="p-6">
            <h3 class="text-white text-[20px] font-normal mb-1">
              {{ member.name }}
            </h3>
            <div class="text-[#d4af37] text-sm tracking-[0.6px] mb-2">
              {{ member.role }}
            </div>
            <p class="text-white/75 text-sm leading-6">{{ member.bio }}</p>
          </div>
        </article>
      </div>
    </div>
  </section>
</template>

<script setup>
import imgA from "../assets/images/Menna.png";
import imgB from "../assets/images/Raghad.png";
import imgC from "../assets/images/Afnaan.png";
import imgD from "../assets/images/shahed.png";

const team = [
  {
    name: "Menna, 22",
    role: "Website Designer",
    bio: "Creative designer specializing in cinematic web experiences. Passionate about storytelling through design and bringing narratives to life.",
    image: imgA,
  },
  {
    name: "Raghad, 22",
    role: "Web Developer",
    bio: "Full-stack developer with expertise in modern web technologies. Focused on creating seamless, responsive user experiences.",
    image: imgB,
  },
  {
    name: "Afnan, 22",
    role: "Photographer",
    bio: "Documentary photographer capturing authentic moments and powerful human stories. Specialized in portraiture and narrative photography.",
    image: imgC,
  },
  {
    name: "Shahd, 22",
    role: "Video Editor",
    bio: "Expert video editor crafting compelling visual narratives. Skilled in color grading, motion graphics, and emotional storytelling.",
    image: imgD,
  },
];
</script>
