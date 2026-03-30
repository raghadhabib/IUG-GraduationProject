<template>
  <section
    class="flex flex-col items-center md:justify-center relative md:pt-20 pb-20 md:pb-0 w-full h-full overflow-hidden bg-black"
  >
    <div class="relative z-10 max-w-1400 w-[90%] mx-auto px-4 md:px-8 lg:pt-8">
      <!-- Header -->
      <div class="mb-6 max-w-275">
        <h2
          class="text-6xl lg:text-5xl text-white font-normal -tracking-[1px] drop-shadow-[0_10px_30px_rgba(0,0,0,0.6)] mb-2"
        >
          The Team
        </h2>
        <p class="text-white/65 text-base max-w-[900px]">
          The people who made this film happen.
        </p>
      </div>

      <!-- Team grid -->
      <div class="team-grid grid grid-cols-2 md:grid-cols-4 gap-3 lg:gap-6">
        <a
          v-for="(member, idx) in team"
          :key="idx"
          :href="member.linkedinUrl"
          target="_blank"
          rel="noopener noreferrer"
          class="group overflow-hidden rounded-md bg-[rgba(255,255,255,0.02)] border border-[rgba(212,175,55,0.06)] transform transition-all duration-300 will-change-transform hover:shadow-2xl hover:border-[rgba(212,175,55,0.3)] cursor-pointer no-underline"
        >
          <div class="relative w-full aspect-square overflow-hidden bg-[#111]">
            <img
              :src="member.image"
              :alt="member.name"
              class="w-full h-full object-cover block transition-transform duration-300 ease-in-out origin-center"
            />
            <div
              class="absolute inset-0 bg-gradient-to-b from-transparent via-black/30 to-black/75 pointer-events-none"
            ></div>

            <div
              class="absolute inset-0 flex items-center justify-center opacity-0 group-hover:opacity-100 transition-opacity duration-300 bg-black/80"
            >
              <div class="bg-black border-2 border-black rounded-md p-2">
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  width="28"
                  height="28"
                  viewBox="0 0 24 24"
                  fill="white"
                >
                  <path
                    d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433a2.062 2.062 0 0 1-2.063-2.065 2.064 2.064 0 1 1 2.063 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"
                  />
                </svg>
              </div>
            </div>
          </div>

          <div class="p-2 md:p-3 lg:p-6">
            <h3
              class="text-white text-sm md:text-sm lg:text-[20px] font-normal mb-0.5 lg:mb-1"
            >
              {{ member.name }}
            </h3>
            <div class="text-[#d4af37] text-xs tracking-[0.6px] mb-1 lg:mb-2">
              {{ member.role }}
            </div>
            <p
              class="text-white/75 text-xs lg:text-sm leading-5 hidden lg:block"
            >
              {{ member.bio }}
            </p>
          </div>
        </a>
      </div>

      <!-- Copyright footer -->
      <div
        class="w-full md:static fixed bottom-0 right-0 left-0 mt-5 mb-4 py-5 border-t border-white/10 flex items-center justify-center"
      >
        <p class="text-white/50 text-xs tracking-[2px] text-center">
          &nbsp; &copy; {{ new Date().getFullYear() }} All Rights Reserved.
        </p>
      </div>
    </div>
  </section>
</template>

<script setup>
import imgA from "../assets/images/mennaGrad2.webp";
import imgB from "../assets/images/raghedGrad copy.webp";
import imgC from "../assets/images/afnaan.jpeg";
import imgD from "../assets/images/shahedGrad copy.webp";

const team = [
  {
    name: "Menna Baker",
    role: "Website Designer",
    bio: "Menna shaped the visual identity of this project — every layout and color choice was intentional.",
    image: imgA,
    linkedinUrl: "https://www.linkedin.com/in/menna-baker/",
  },
  {
    name: "Raghad Habib",
    role: "Front-End Developer",
    bio: "Raghad built the website from the ground up, turning design into a smooth, responsive product.",
    image: imgB,
    linkedinUrl: "https://www.linkedin.com/in/raghadhabib/",
  },
  {
    name: "Afnan Al-ashqar",
    role: "Film Maker",
    bio: "Afnan is behind the camera — she directed the documentary and captured something honest in every frame.",
    image: imgC,
    linkedinUrl: "https://www.linkedin.com/in/afnan-ashqar-5591b7239/",
  },
  {
    name: "Shahd Alayobi",
    role: "Video Editor",
    bio: "Shahd gave the footage its final shape — through her editing, the film found its rhythm and emotional weight.",
    image: imgD,
    linkedinUrl:
      "https://www.linkedin.com/in/%D8%B4%D9%87%D8%AF-%D8%A7%D9%84%D8%A7%D9%8A%D9%88%D8%A8%D9%8A-326a55395/",
  },
];
</script>
