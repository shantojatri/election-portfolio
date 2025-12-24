<script setup lang="ts">
import { ref, onMounted, onUnmounted } from "vue";
import { useRoute } from "vue-router";

const activeSection = ref("home");
const route = useRoute();

const handleScroll = () => {
  const sections = [
    "home",
    "about",
    "manifesto",
    "donate",
    "24-dofa-ncp",
    "reform",
  ];
  const scrollPosition = window.scrollY + 100; // Adjust based on navbar height

  sections.forEach((section) => {
    const el = document.getElementById(section);
    if (el) {
      const offsetTop = el.offsetTop;
      const offsetHeight = el.offsetHeight;

      if (
        scrollPosition >= offsetTop &&
        scrollPosition < offsetTop + offsetHeight
      ) {
        activeSection.value = section;
      }
    }
  });
};

onMounted(() => {
  window.addEventListener("scroll", handleScroll);
});
onUnmounted(() => {
  window.removeEventListener("scroll", handleScroll);
});

const isMenuOpen = ref(false);
const navLinks = [
  { name: "হোম", href: "/", id: "home" },
  { name: "পরিচিতি", href: "/#about", id: "about" },
  { name: "ইশতেহার", href: "/#manifesto", id: "manifesto" },
  { name: "অনুদান", href: "/#donate", id: "donate" },
  { name: "এনসিপির ২৪ দফা", href: "/24-dofa-ncp", id: "24-dofa-ncp" },
  { name: "গণভোটে প্রস্তাবিত সংস্কারসমূহ", href: "/reform", id: "reform" },
];

const closeMenu = () => {
  isMenuOpen.value = false;
};
</script>
<template>
  <nav
    class="bg-green-700 sticky top-0 left-0 right-0 z-50 text-white shadow-md"
  >
    <div class="container mx-auto px-4 py-3 flex justify-between items-center">
      <div class="text-xl md:text-2xl font-bold flex items-center gap-2">
        <span>অ্যাডভোকেট আনিকা নার্গিস</span>
      </div>

      <div class="hidden md:flex space-x-6 font-medium">
        <NuxtLink
          v-for="link in navLinks"
          :key="link.name"
          :to="link.href"
          :class="[
            'transition duration-300 pb-1 border-b-2',
            route.fullPath === link.href
              ? 'text-yellow-400 border-yellow-400'
              : 'text-white border-transparent hover:text-yellow-400',
          ]"
        >
          {{ link.name }}
        </NuxtLink>
      </div>

      <div class="flex items-center gap-3">
        <NuxtLink
          to="/#donate"
          class="hidden sm:block bg-yellow-400 text-green-900 px-5 py-2 rounded-full font-bold hover:bg-yellow-300 transition text-sm"
        >
          সমর্থন করুন
        </NuxtLink>

        <button
          @click="isMenuOpen = !isMenuOpen"
          class="md:hidden p-2 text-white focus:outline-none"
          aria-label="Toggle Menu"
        >
          <svg
            xmlns="http://www.w3.org/2000/svg"
            class="h-8 w-8"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
          >
            <path
              v-if="!isMenuOpen"
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M4 6h16M4 12h16m-7 6h7"
            />
            <path
              v-else
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M6 18L18 6M6 6l12 12"
            />
          </svg>
        </button>
      </div>
    </div>

    <transition name="slide">
      <div
        v-if="isMenuOpen"
        class="md:hidden bg-green-800 border-t border-green-600"
      >
        <div class="flex flex-col p-4 space-y-4 font-medium text-center">
          <a
            v-for="link in navLinks"
            :key="link.name"
            :href="link.href"
            @click="closeMenu"
            class="block py-2 border-b border-green-700 hover:text-yellow-400"
          >
            {{ link.name }}
          </a>
          <a
            href="#donate"
            @click="closeMenu"
            class="bg-yellow-400 text-green-900 py-3 rounded-lg font-bold"
          >
            সমর্থন করুন
          </a>
        </div>
      </div>
    </transition>
  </nav>
</template>
