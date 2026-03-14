<template>
  <section class="flex flex-col items-center justify-center relative pt-20 w-full h-full overflow-hidden bg-black">
    <div class="relative z-10 max-w-1400 w-[90%] mx-auto px-8 pt-8">
      <!-- Header -->
      <div class="mb-6 max-w-275">
        <h2
          class="text-6xl lg:text-5xl text-white font-normal -tracking-[1px] drop-shadow-[0_10px_30px_rgba(0,0,0,0.6)] mb-4"
        >
          The Team
        </h2>
        <p class="text-white/65 text-base max-w-[900px]">
          The visionaries and artists who brought this story to life.
        </p>
      </div>

      <!-- Team grid -->
      <div class="team-grid grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-10">
        <a
          v-for="(member, idx) in team"
          :key="idx"
          :href="member.linkedinUrl"
          target="_blank"
          rel="noopener noreferrer"
          class="group overflow-hidden rounded-md bg-[rgba(255,255,255,0.02)] border border-[rgba(212,175,55,0.06)] transform transition-all duration-300 will-change-transform hover:shadow-2xl hover:border-[rgba(212,175,55,0.3)] cursor-pointer no-underline"
        >
          <div class="relative w-[250px] h-[250px] overflow-hidden mx-auto bg-[#111]">
            <img
              :src="member.image"
              :alt="member.name"
              class="w-full h-[260px] object-cover block transition-transform duration-300 ease-in-out origin-center "
            />
            <div
              class="absolute inset-0 bg-gradient-to-b from-transparent via-black/30 to-black/75 pointer-events-none"
            ></div>

            <div class="absolute inset-0 flex items-center justify-center opacity-0 group-hover:opacity-100 transition-opacity duration-300 bg-black/80">
              <div class="bg-black border-2 border-black rounded-md p-2">
                <svg xmlns="http://www.w3.org/2000/svg" width="28" height="28" viewBox="0 0 24 24" fill="white">
                  <path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433a2.062 2.062 0 0 1-2.063-2.065 2.064 2.064 0 1 1 2.063 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/>
                </svg>
              </div>
            </div>
          </div>

          <div class="p-6">
            <h3 class="text-white text-[20px] font-normal mb-1">{{ member.name }}</h3>
            <div class="text-[#d4af37] text-sm tracking-[0.6px] mb-2">{{ member.role }}</div>
            <p class="text-white/75 text-sm leading-6">{{ member.bio }}</p>
          </div>
        </a>
      </div>

      <!-- Copyright footer -->
      <div class="w-full mt-5 mb-4 py-5 border-t border-white/10 flex items-center justify-center">
        <p class="text-white/50 text-xs tracking-[2px] text-center">
          &nbsp; &copy; {{ new Date().getFullYear() }} All Rights Reserved.
        </p>
      </div>
    </div>
  </section>
</template>

<script setup>
import imgA from "../assets/images/mennaGrad2.png";
import imgB from "../assets/images/Raghad Grad.png";
import imgC from "../assets/images/AfnanGrad.png";
import imgD from "../assets/images/shahed.png";

const team = [
  {
    name: "Menna Baker",
    role: "Website Designer",
    bio: "Creative designer specializing in cinematic web experiences. Passionate about storytelling through design and bringing narratives to life.",
    image: imgA,
    linkedinUrl: "https://www.linkedin.com/in/menna-baker/",
  },
  {
    name: "Raghad Habib",
    role: "Front-End Dev",
    bio: "Front-End developer with expertise in modern web technologies. Focused on creating seamless, responsive user experiences.",
    image: imgB,
    linkedinUrl: "https://www.linkedin.com/in/raghadhabib/",
  },
  {
    name: "Afnan Al-ahqar",
    role: "Film maker",
    bio: "Documentary photographer capturing authentic moments and powerful human stories. Specialized in portraiture and narrative photography.",
    image: imgC,
    linkedinUrl: "https://www.linkedin.com/in/afnan-ashqar-5591b7239/",
  },
  {
    name: "Shahd Alayobi",
    role: "Video Editor",
    bio: "Expert video editor crafting compelling visual narratives. Skilled in color grading, motion graphics, and emotional storytelling.",
    image: imgD,
    linkedinUrl: "https://www.linkedin.com/in/%D8%B4%D9%87%D8%AF-%D8%A7%D9%84%D8%A7%D9%8A%D9%88%D8%A8%D9%8A-326a55395/",
  },
];
</script>