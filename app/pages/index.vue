<script setup>
import { ref } from "vue";

const showVideo = ref(false);
const stats = [
  { value: "১৫০০+", label: "স্বেচ্ছাসেবক" },
  { value: "৫,০০০+", label: "সমর্থক" },
  { value: "২১", label: "গ্রাম কভার" },
  { value: "৮", label: "জনসভা সম্পন্ন" },
];

const manifestoItems = [
  {
    icon: "🎓",
    title: "শিক্ষা খাত",
    points: [
      "ডিজিটাল ক্লাসরুম স্থাপন",
      "বিনামূল্যে বই বিতরণ",
      "কম্পিউটার প্রশিক্ষণ কেন্দ্র",
    ],
  },
  {
    icon: "🏥",
    title: "স্বাস্থ্যসেবা",
    points: [
      "আধুনিক উপজেলা হাসপাতাল",
      "মোবাইল মেডিকেল টিম",
      "মাতৃস্বাস্থ্য কার্ড",
    ],
  },
  {
    icon: "🛣️",
    title: "অবকাঠামো",
    points: ["গ্রামীণ সড়ক উন্নয়ন", "নিরাপদ পানীয় জল", "সৌর সড়ক বাতি"],
  },
  {
    icon: "💼",
    title: "যুব ও কর্মসংস্থান",
    points: [
      "স্বল্পসুদে বেকার ঋণ",
      "কারিগরি প্রশিক্ষণ",
      "আইটি ফ্রিল্যান্সিং জোন",
    ],
  },
  {
    icon: "🌾",
    title: "কৃষি উন্নয়ন",
    points: [
      "সার ও বীজে ভর্তুকি",
      "আধুনিক সেচ ব্যবস্থা",
      "কোল্ড স্টোরেজ সুবিধা",
    ],
  },
  {
    icon: "👩",
    title: "নারী উন্নয়ন",
    points: ["নারী উদ্যোক্তা ঋণ", "সিসিটিভি নিরাপত্তা", "বিধবা ভাতা সংস্কার"],
  },
];

// 3. QR Code Logic
const websiteUrl = "https://engrnabiladhaka20.com";
const qrCodeUrl = `https://api.qrserver.com/v1/create-qr-code/?size=1000x1000&data=${encodeURIComponent(
  websiteUrl
)}&ecc=M&margin=0`;
</script>

<template>
  <section id="home" class="relative bg-green-800 text-white overflow-hidden">
    <div class="absolute inset-0 opacity-10">
      <div
        class="absolute -right-20 -top-20 w-96 h-96 bg-yellow-400 rounded-full blur-3xl"
      ></div>
    </div>

    <div
      class="container mx-auto px-4 py-10 md:py-24 flex flex-col md:flex-row items-center relative z-10"
    >
      <div
        class="w-full md:w-3/4 mb-10 md:mb-0 text-center md:text-left order-2 md:order-1"
      >
        <span
          class="bg-yellow-400 text-green-900 px-4 py-1 rounded-full font-bold text-sm uppercase tracking-wider"
          >টাঙ্গাইল-২ (গোপালপুর - ভূঞাপুর)</span
        >

        <h1 class="text-3xl md:text-6xl font-extrabold mt-4 leading-tight">
          উন্নত ও আধুনিক <br />
          <span class="text-yellow-400">গোপালপুর-ভূঞাপুর</span> গড়ার প্রত্যয়
        </h1>
        <p
          class="text-base md:text-lg mt-6 text-gray-200 max-w-2xl mx-auto md:mx-0"
        >
          জনগণের ভোটে নির্বাচিত হতে চাই, জনগণের সাথে থাকবো, জনগণের জন্য কাজ
          করবো। আপনার একটি ভোটই হতে পারে আগামীর পরিবর্তনের চাবিকাঠি।
        </p>

        <div class="flex flex-col md:flex-row items-center gap-4 mt-4 mb-6">
          <img
            src="https://upload.wikimedia.org/wikipedia/commons/e/e6/58-shapla-koli-protik-1.jpg"
            alt="Shapla Koli Symbol"
            class="w-20 h-20 md:w-28 md:h-28 rounded-full border-4 border-yellow-400 bg-white object-contain shadow-xl"
          />
          <div class="text-center md:text-left">
            <h2
              class="text-2xl md:text-4xl font-bold mt-2 text-yellow-300 italic drop-shadow-md"
            >
              "শাপলাকলি মার্কায় ভোট দিন"
            </h2>
          </div>
        </div>
        <div
          class="mt-8 flex flex-col sm:flex-row gap-4 justify-center md:justify-start"
        >
          <NuxtLink
            to="/24-dofa-ncp#join-ncp"
            class="bg-yellow-400 text-green-900 px-8 py-4 rounded-lg font-bold text-lg hover:shadow-xl transform hover:-translate-y-1 transition-all"
          >
            যোগদান করুন
          </NuxtLink>
          <button
            @click="showVideo = true"
            class="border-2 border-white px-8 py-4 rounded-lg font-bold text-lg hover:bg-white hover:text-green-800 transition-all"
          >
            ভিডিও বার্তা
          </button>
        </div>
      </div>

      <div
        class="w-full md:w-1/4 flex justify-center order-1 md:order-2 mb-8 md:mb-0"
      >
        <div class="relative w-48 h-48 sm:w-64 sm:h-64 lg:w-80 lg:h-80">
          <div
            class="absolute inset-0 bg-yellow-400 rounded-full scale-110 blur-md opacity-30"
          ></div>
          <img
            src="https://picsum.photos/500/500"
            alt="Candidate"
            class="relative z-10 w-full h-full rounded-full border-4 md:border-8 border-white shadow-2xl object-cover"
          />
        </div>
      </div>
    </div>

    <transition name="fade">
      <div
        v-if="showVideo"
        class="fixed inset-0 z-[100] flex items-center justify-center bg-black/95 p-2 md:p-6"
        @click.self="showVideo = false"
      >
        <div
          class="relative w-full max-w-4xl aspect-video bg-black rounded-xl overflow-hidden"
        >
          <button
            @click="showVideo = false"
            class="absolute top-2 right-2 z-10 bg-yellow-400 text-black w-10 h-10 rounded-full font-bold"
          >
            ✕
          </button>
          <iframe
            class="w-full h-full"
            src="https://www.youtube.com/embed/8-FkhfTOxB4?autoplay=1"
            frameborder="0"
            allowfullscreen
          ></iframe>
        </div>
      </div>
    </transition>
  </section>

  <section id="about" class="py-16 md:py-24 container mx-auto px-4">
    <div class="text-center mb-12">
      <h2 class="text-3xl font-bold text-green-800">প্রার্থী পরিচিতি</h2>
      <div class="w-24 h-1 bg-yellow-500 mx-auto mt-2"></div>
    </div>
    <div class="grid md:grid-cols-2 gap-12 items-center">
      <div class="order-2 md:order-1">
        <h3 class="text-2xl font-bold mb-4 text-green-700">
          অ্যাডভোকেট আনিকা নার্গিস
        </h3>
        <p class="text-gray-600 leading-relaxed mb-6">
          দীর্ঘ এক দশক ধরে আপনাদের পাশে থেকে সামাজিক কর্মকাণ্ডে নিজেকে নিয়োজিত
          রেখেছি। জনগণের অধিকার আদায়ে আইনি লড়াইয়ের পাশাপাশি এলাকাভিত্তিক
          উন্নয়নে আমি বদ্ধপরিকর। আমার লক্ষ্য—একটি স্বচ্ছ এবং দুর্নীতিমুক্ত
          গোপালপুর-ভূঞাপুর গড়ে তোলা।
        </p>
        <ul class="space-y-4">
          <li
            v-for="point in [
              'উচ্চ শিক্ষা ও আধুনিক চিন্তা',
              'তৃণমূলের সাথে গভীর সম্পর্ক',
              'স্বচ্ছ ও জবাবদিহিমূলক নেতৃত্ব',
            ]"
            :key="point"
            class="flex items-center gap-3"
          >
            <span class="bg-green-100 text-green-600 p-1 rounded-full">✔</span>
            <span class="font-medium">{{ point }}</span>
          </li>
        </ul>
      </div>
      <div
        class="bg-green-50 p-6 md:p-10 rounded-3xl border-l-8 border-yellow-400 order-1 md:order-2 shadow-sm"
      >
        <h4 class="font-bold text-xl mb-6 text-green-800">
          প্রধান অঙ্গীকারসমূহ
        </h4>
        <div class="space-y-4">
          <div
            v-for="item in [
              '🎓 শিক্ষার আধুনিকায়ন ও উপবৃত্তি',
              '🏥 মানসম্মত স্বাস্থ্যসেবা নিশ্চিতকরণ',
              '🛣️ গ্রামীণ রাস্তাঘাট উন্নয়ন',
            ]"
            :key="item"
            class="bg-white p-4 rounded-xl shadow-sm font-medium border border-green-100"
          >
            {{ item }}
          </div>
        </div>
      </div>
    </div>
  </section>

  <section id="manifesto" class="py-16 bg-white">
    <div class="container mx-auto px-4">
      <div class="text-center mb-16">
        <h2 class="text-4xl font-bold text-green-800 mb-4">
          নির্বাচনী ইশতেহার ২০২৬
        </h2>
        <p class="text-xl text-gray-600">উন্নয়ন ও সমৃদ্ধির রোডম্যাপ</p>
        <div class="w-24 h-1.5 bg-yellow-400 mx-auto mt-4 rounded-full"></div>
      </div>

      <div
        class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6 md:gap-8"
      >
        <div
          v-for="(item, index) in manifestoItems"
          :key="index"
          class="manifesto-card group"
        >
          <div class="icon-box">{{ item.icon }}</div>
          <h3 class="text-2xl font-bold text-green-700 mb-3">
            {{ item.title }}
          </h3>
          <ul class="space-y-2 text-gray-700 text-sm md:text-base">
            <li v-for="point in item.points" :key="point">• {{ point }}</li>
          </ul>
        </div>
      </div>
    </div>
  </section>

  <section class="py-16 bg-green-800 text-white">
    <div class="container mx-auto px-4">
      <div class="text-center mb-12">
        <h2 class="text-3xl md:text-4xl font-bold mb-4">
          আপনার সমর্থন আমাদের শক্তি
        </h2>
        <p class="text-yellow-400 text-lg md:text-2xl">
          একসাথে গড়ে তুলি উন্নত গোপালপুর - ভূঞাপুর
        </p>
      </div>
      <div class="grid grid-cols-2 lg:grid-cols-4 gap-4 md:gap-8">
        <div v-for="stat in stats" :key="stat.label" class="stat-card p-6">
          <div class="text-yellow-400 text-3xl md:text-5xl font-black mb-1">
            {{ stat.value }}
          </div>
          <p class="text-gray-200 text-sm md:text-lg">{{ stat.label }}</p>
        </div>
      </div>
    </div>
  </section>

  <section
    id="donate"
    class="bg-gray-50 py-16 md:py-24 border-t border-gray-200"
  >
    <div class="container mx-auto px-4">
      <div
        class="max-w-4xl mx-auto bg-white rounded-3xl shadow-2xl overflow-hidden flex flex-col md:flex-row"
      >
        <div
          class="md:w-1/3 bg-green-700 p-8 text-center text-white flex flex-col justify-center items-center"
        >
          <h3 class="text-xl font-bold mb-4">ওয়েবসাইট কিউআর</h3>
          <div class="bg-white p-2 rounded-xl mb-4 shadow-inner">
            <img
              :src="qrCodeUrl"
              alt="Website QR"
              class="w-40 h-40"
              style="image-rendering: pixelated"
            />
          </div>
          <p class="text-xs opacity-80 leading-relaxed">
            মোবাইল ক্যামেরা দিয়ে স্ক্যান করে প্রচারণায় অংশ নিন
          </p>
        </div>

        <div class="md:w-2/3 p-8 md:p-12">
          <h2 class="text-3xl font-bold text-green-800 mb-6">
            নির্বাচনী অনুদান
          </h2>
          <div class="space-y-8">
            <div class="bg-green-50 p-5 rounded-2xl border border-green-100">
              <h4 class="font-bold text-gray-800 mb-2">ব্যাংক একাউন্ট</h4>
              <p class="text-sm text-gray-700">নাম: অ্যাডভোকেট আনিকা নার্গিস</p>
              <p class="text-sm text-gray-700">
                ব্যাংক: ডাচ-বাংলা ব্যাংক লিমিটেড
              </p>
              <p class="text-lg font-mono font-bold text-green-700 mt-2">
                ২০৩.১৫১.০৯৮৭৬
              </p>
            </div>

            <div class="grid grid-cols-2 gap-3">
              <div
                v-for="mfs in ['bKash', 'Nagad', 'Rocket', 'Upay']"
                :key="mfs"
                class="p-3 border rounded-xl bg-white shadow-sm text-center"
              >
                <p class="font-bold text-sm text-gray-800">{{ mfs }}</p>
                <p class="text-xs text-green-600 font-bold">01959263946</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
@reference "~/assets/main/main.css";

html {
  scroll-behavior: smooth !important;
}

.stat-card {
  @apply flex flex-col items-center justify-center border border-green-700 rounded-2xl bg-green-900/50 hover:bg-green-700 transition-colors duration-300;
}

.manifesto-card {
  @apply p-6 md:p-8 bg-white border-b-4 border-yellow-400 rounded-2xl shadow-lg hover:bg-green-50 transition-all duration-300;
}

.icon-box {
  @apply w-12 h-12 md:w-16 md:h-16 bg-yellow-100 text-2xl md:text-3xl flex items-center justify-center rounded-xl mb-6;
}

/* Animations for Mobile Menu */
.slide-enter-active,
.slide-leave-active {
  transition: all 0.3s ease;
}
.slide-enter-from,
.slide-leave-to {
  opacity: 0;
  transform: translateY(-10px);
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>
