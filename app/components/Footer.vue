<script setup lang="ts">
const navLinks = [
  { name: "হোম", href: "#home" },
  { name: "পরিচিতি", href: "#about" },
  { name: "ইশতেহার", href: "#manifesto" },
  { name: "অনুদান", href: "#donate" },
];

const currentYear = new Date().getFullYear();
</script>
<template>
  <footer class="bg-green-900 text-white pt-16 pb-8">
    <div class="container mx-auto px-4">
      <div class="grid grid-cols-1 md:grid-cols-3 gap-12 mb-12">
        <div class="text-center md:text-left space-y-5">
          <div class="bg-white p-2 rounded-xl inline-block shadow-lg">
            <img src="/images/ncpbd.png" alt="NCP Logo" class="h-32 w-auto" />
          </div>
          <h3 class="text-xl font-bold text-white">
            জাতীয় নাগরিক পার্টি (NCP)
          </h3>
          <p class="text-gray-300 text-sm leading-relaxed">
            জনগণের উন্নয়ন ও অগ্রগতিই আমাদের মূল লক্ষ্য। আপনার মূল্যবান ভোট দিয়ে
            পরিবর্তনের সঙ্গী হোন।
          </p>
        </div>

        <div class="text-center md:text-left">
          <h4
            class="text-lg font-bold mb-6 text-yellow-500 border-b border-green-800 pb-2 inline-block"
          >
            লিংকসমূহ
          </h4>
          <ul class="space-y-3 text-sm">
            <li v-for="link in navLinks" :key="link.name">
              <a
                :href="link.href"
                class="text-gray-300 hover:text-yellow-400 transition"
                >{{ link.name }}</a
              >
            </li>
          </ul>
        </div>

        <div id="contact" class="text-center md:text-left">
          <h4
            class="text-lg font-bold mb-6 text-yellow-500 border-b border-green-800 pb-2 inline-block"
          >
            যোগাযোগ
          </h4>
          <ul class="space-y-4 text-sm text-gray-300">
            <li class="flex justify-center md:justify-start items-center gap-3">
              <span class="text-yellow-400 text-xl">📍</span> গোপালপুর উপজেলা,
              টাঙ্গাইল
            </li>
            <li class="flex justify-center md:justify-start items-center gap-3">
              <span class="text-yellow-400 text-xl">📞</span> ০১৯৫৯-২৬৩৯৪৬,
              ০১৭৫৩-১৫২৪০১
            </li>
          </ul>
        </div>
      </div>

      <div
        class="border-t border-green-800 pt-8 flex justify-center text-center text-sm text-gray-400 px-4"
      >
        <p>
          © {{ currentYear }} অ্যাডভোকেট আনিকা নার্গিস এর প্রচারণা। সর্বস্বত্ব
          সংরক্ষিত।
        </p>
      </div>
    </div>
  </footer>
</template>
