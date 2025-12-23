<script setup>
import { ref } from "vue";

// State to control the visibility of the video modal
const showVideo = ref(false);
const currentYear = new Date().getFullYear();
// Generate a real QR code using a service like QR Server
const websiteUrl = "https://engrnabiladhaka20.com";

// 1. Increased size to 1000x1000 for maximum clarity
// 2. Removed color parameter (defaults to pure black #000000)
// 3. ecc=M (Medium error correction for a cleaner, less dense pattern)
const qrCodeUrl = `https://api.qrserver.com/v1/create-qr-code/?size=1000x1000&data=${encodeURIComponent(
  websiteUrl
)}&ecc=M&margin=0`;
</script>

<template>
  <div class="min-h-screen bg-gray-50 font-sans text-gray-900">
    <nav class="bg-green-700 text-white sticky top-0 z-50 shadow-md">
      <div
        class="container mx-auto px-4 py-3 flex justify-between items-center"
      >
        <div class="text-2xl font-bold flex items-center gap-2">
          <!-- <div
            class="w-10 h-10 bg-yellow-400 rounded-full flex items-center justify-center text-green-800"
          >
            LOGO
          </div> -->
          <span>অ্যাডভোকেট আনিকা নার্গিস</span>
        </div>
        <div class="hidden md:flex space-x-6 font-medium">
          <a href="#home" class="hover:text-yellow-400 transition">হোম</a>
          <a href="#about" class="hover:text-yellow-400 transition">পরিচিতি</a>
          <a href="#manifesto" class="hover:text-yellow-400 transition"
            >ইশতেহার</a
          >
          <a href="#donate" class="hover:text-yellow-400 transition">অনুদান</a>
        </div>
        <a
          href="#donate"
          class="bg-yellow-400 text-green-900 px-6 py-2 rounded-full font-bold hover:bg-yellow-300 transition"
        >
          সমর্থন করুন
        </a>
      </div>
    </nav>

    <section id="home" class="relative bg-green-800 text-white overflow-hidden">
      <div class="absolute inset-0 opacity-20">
        <div
          class="absolute -right-20 -top-20 w-96 h-96 bg-yellow-400 rounded-full blur-3xl"
        ></div>
      </div>

      <div
        class="container mx-auto px-4 py-16 md:py-24 flex flex-col md:flex-row items-center relative z-10"
      >
        <div class="md:w-3/4 mb-10 md:mb-0">
          <span
            class="bg-yellow-400 text-green-900 px-4 py-1 rounded-full font-bold text-sm uppercase tracking-wider"
            >টাঙ্গাইল-২ (গোপালপুর - ভূঞাপুর)</span
          >
          <h1 class="text-4xl md:text-6xl font-extrabold mt-4 leading-tight">
            উন্নত ও আধুনিক <br />
            <span class="text-yellow-400">গোপালপুর-ভূঞাপুর</span> গড়ার প্রত্যয়
          </h1>
          <p class="text-lg mt-6 text-gray-200">
            জনগণের ভোটে নির্বাচিত হতে চাই, জনগণের সাথে থাকবো, জনগণের জন্য কাজ
            করবো। আপনার একটি ভোটই হতে পারে আগামীর পরিবর্তনের চাবিকাঠি।
          </p>
          <div class="mt-8 flex gap-4">
            <button
              class="bg-yellow-400 text-green-900 px-8 py-3 rounded-lg font-bold text-lg hover:shadow-lg transform hover:-translate-y-1 transition"
            >
              যোগদান করুন
            </button>
            <button
              @click="showVideo = true"
              class="border-2 border-white px-8 py-3 rounded-lg font-bold text-lg hover:bg-white hover:text-green-800 transition"
            >
              ভিডিও বার্তা
            </button>

            <div
              v-if="showVideo"
              class="fixed inset-0 z-[100] flex items-center justify-center bg-black/90 p-4"
              @click.self="showVideo = false"
            >
              <div
                class="relative w-full max-w-4xl aspect-video bg-black rounded-xl overflow-hidden shadow-2xl"
              >
                <button
                  @click="showVideo = false"
                  class="absolute top-4 right-4 z-10 bg-yellow-400 text-black w-10 h-10 rounded-full font-bold hover:bg-yellow-300 transition"
                >
                  ✕
                </button>

                <iframe
                  class="w-full h-full"
                  src="https://www.youtube.com/embed/8-FkhfTOxB4?autoplay=1"
                  title="NCP Video Message"
                  frameborder="0"
                  allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
                  allowfullscreen
                ></iframe>
              </div>
            </div>
          </div>
        </div>
        <div class="md:w-1/4 flex justify-center">
          <div class="relative">
            <div
              class="absolute inset-0 bg-yellow-400 rounded-full scale-105 blur-sm"
            ></div>
            <img
              src="https://picsum.photos/500/500"
              alt="Candidate"
              class="relative z-10 rounded-2xl border-4 border-white shadow-2xl object-cover"
            />
          </div>
        </div>
      </div>
    </section>

    <section id="about" class="py-20 container mx-auto px-4">
      <div class="text-center mb-16">
        <h2 class="text-3xl font-bold text-green-800">প্রার্থী পরিচিতি</h2>
        <div class="w-24 h-1 bg-yellow-500 mx-auto mt-2"></div>
      </div>
      <div class="grid md:grid-cols-2 gap-12 items-center">
        <div>
          <h3 class="text-2xl font-bold mb-4">অ্যাডভোকেট আনিকা নার্গিস</h3>
          <p class="text-gray-600 leading-relaxed mb-6">
            দীর্ঘ এক দশক ধরে আপনাদের পাশে থেকে সামাজিক কর্মকাণ্ডে নিজেকে নিয়োজিত
            রেখেছি। পেশায় একজন প্রকৌশলী হওয়ায় আধুনিক নগর পরিকল্পনা ও অবকাঠামোগত
            উন্নয়নে আমার বিশেষ দক্ষতা রয়েছে। আমার লক্ষ্য—একটি স্বচ্ছ, ডিজিটাল
            এবং দুর্নীতিমুক্ত ধামরাই গড়ে তোলা।
          </p>
          <ul class="space-y-3">
            <li class="flex items-center gap-2">
              <span class="text-green-600">✔</span> উচ্চ শিক্ষা ও আধুনিক চিন্তা
            </li>
            <li class="flex items-center gap-2">
              <span class="text-green-600">✔</span> তৃণমূলের সাথে গভীর সম্পর্ক
            </li>
            <li class="flex items-center gap-2">
              <span class="text-green-600">✔</span> স্বচ্ছ ও জবাবদিহিমূলক
              নেতৃত্ব
            </li>
          </ul>
        </div>
        <div class="bg-green-50 p-8 rounded-2xl border-l-8 border-yellow-400">
          <h4 class="font-bold text-xl mb-4 text-green-800">
            প্রধান অঙ্গীকারসমূহ
          </h4>
          <div class="grid grid-cols-1 gap-4">
            <div class="bg-white p-4 rounded shadow-sm">
              🎓 শিক্ষার আধুনিকায়ন ও উপবৃত্তি
            </div>
            <div class="bg-white p-4 rounded shadow-sm">
              🏥 মানসম্মত স্বাস্থ্যসেবা নিশ্চিতকরণ
            </div>
            <div class="bg-white p-4 rounded shadow-sm">
              🛣️ গ্রামীণ রাস্তাঘাট উন্নয়ন
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
          <p class="text-xl text-gray-600">
            টাঙ্গাইল-২ আসনের উন্নয়ন ও সমৃদ্ধির রোডম্যাপ
          </p>
          <div class="w-24 h-1.5 bg-yellow-400 mx-auto mt-4 rounded-full"></div>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
          <div class="manifesto-card group">
            <div class="icon-box">🎓</div>
            <h3 class="text-2xl font-bold text-green-700 mb-3">শিক্ষা খাত</h3>
            <ul class="space-y-2 text-gray-700">
              <li>
                • প্রতিটি মাধ্যমিক বিদ্যালয়ে <b>ডিজিটাল ক্লাসরুম</b> স্থাপন।
              </li>
              <li>• দরিদ্র শিক্ষার্থীদের বিনামূল্যে বই ও ইউনিফর্ম বিতরণ।</li>
              <li>
                • উপজেলা পর্যায়ে আধুনিক
                <b>ভাষা ও কম্পিউটার প্রশিক্ষণ</b> কেন্দ্র।
              </li>
            </ul>
          </div>

          <div class="manifesto-card group">
            <div class="icon-box">🏥</div>
            <h3 class="text-2xl font-bold text-green-700 mb-3">
              স্বাস্থ্যসেবা
            </h3>
            <ul class="space-y-2 text-gray-700">
              <li>
                • ৫০ শয্যার <b>আধুনিক হাসপাতাল</b> ও যন্ত্রপাতি নিশ্চিতকরণ।
              </li>
              <li>• দুর্গম এলাকায় স্বাস্থ্যসেবায় <b>মোবাইল মেডিকেল টিম</b>।</li>
              <li>• গর্ভবতী মায়েদের জন্য বিশেষ <b>মাতৃস্বাস্থ্য কার্ড</b>।</li>
            </ul>
          </div>

          <div class="manifesto-card group">
            <div class="icon-box">🛣️</div>
            <h3 class="text-2xl font-bold text-green-700 mb-3">অবকাঠামো</h3>
            <ul class="space-y-2 text-gray-700">
              <li>• গ্রামীণ সড়ক উন্নয়ন ও টেকসই ড্রেনেজ ব্যবস্থা।</li>
              <li>• প্রতিটি গ্রামে নিরাপদ পানীয় জল ও স্যানিটেশন।</li>
              <li>• প্রধান বাজারগুলোতে আধুনিক পাবলিক টয়লেট ও লাইটিং।</li>
            </ul>
          </div>

          <div class="manifesto-card group">
            <div class="icon-box">💼</div>
            <h3 class="text-2xl font-bold text-green-700 mb-3">
              কর্মসংস্থান ও যুব
            </h3>
            <ul class="space-y-2 text-gray-700">
              <li>• বেকার যুবকদের জন্য <b>স্বল্পসুদে ঋণ</b> সুবিধা।</li>
              <li>• কারিগরি শিক্ষা ও দক্ষতা উন্নয়ন প্রজেক্ট।</li>
              <li>• ফ্রিল্যান্সিং ও আইটি সেক্টরে বিশেষ প্রণোদনা।</li>
            </ul>
          </div>

          <div class="manifesto-card group">
            <div class="icon-box">🌾</div>
            <h3 class="text-2xl font-bold text-green-700 mb-3">কৃষি উন্নয়ন</h3>
            <ul class="space-y-2 text-gray-700">
              <li>• কৃষকদের জন্য ভর্তুকি মূল্যে সার ও উন্নত বীজ।</li>
              <li>• আধুনিক সেচ ব্যবস্থা ও কোল্ড স্টোরেজ স্থাপন।</li>
              <li>• কৃষি পণ্য সরাসরি বিক্রির জন্য ডিজিটাল প্ল্যাটফর্ম।</li>
            </ul>
          </div>

          <div class="manifesto-card group">
            <div class="icon-box">👩</div>
            <h3 class="text-2xl font-bold text-green-700 mb-3">নারী উন্নয়ন</h3>
            <ul class="space-y-2 text-gray-700">
              <li>• নারী উদ্যোক্তাদের জন্য বিশেষ ব্যবসায়িক জোন।</li>
              <li>
                • নিরাপত্তার জন্য গুরুত্বপূর্ণ স্থানে <b>CCTV ক্যামেরা</b>।
              </li>
              <li>• বিধবা ও দুস্থ মহিলাদের জন্য আত্মনির্ভরশীল প্রকল্প।</li>
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
          <p class="text-yellow-400 text-xl md:text-2xl font-medium">
            একসাথে গড়ে তুলি উন্নত গোপালপুর - ভূঞাপুর
          </p>
          <div class="w-24 h-1 bg-yellow-400 mx-auto mt-6 rounded-full"></div>
        </div>

        <div class="grid grid-cols-2 lg:grid-cols-4 gap-8">
          <div class="stat-card">
            <div
              class="text-yellow-400 text-4xl md:text-5xl font-extrabold mb-2"
            >
              ১৫০০+
            </div>
            <p class="text-gray-200 text-lg md:text-xl">স্বেচ্ছাসেবক</p>
          </div>

          <div class="stat-card">
            <div
              class="text-yellow-400 text-4xl md:text-5xl font-extrabold mb-2"
            >
              ৫,০০০+
            </div>
            <p class="text-gray-200 text-lg md:text-xl">সমর্থক</p>
          </div>

          <div class="stat-card">
            <div
              class="text-yellow-400 text-4xl md:text-5xl font-extrabold mb-2"
            >
              ২১
            </div>
            <p class="text-gray-200 text-lg md:text-xl">গ্রাম কভার</p>
          </div>

          <div class="stat-card">
            <div
              class="text-yellow-400 text-4xl md:text-5xl font-extrabold mb-2"
            >
              ৮
            </div>
            <p class="text-gray-200 text-lg md:text-xl">জনসভা সম্পন্ন</p>
          </div>
        </div>
      </div>
    </section>

    <section id="donate" class="bg-white py-20 border-t border-gray-100">
      <div class="container mx-auto px-4">
        <div
          class="max-w-4xl mx-auto bg-white rounded-3xl shadow-2xl overflow-hidden flex flex-col md:flex-row"
        >
          <div
            class="md:w-1/3 bg-green-700 p-8 text-center text-white flex flex-col justify-center items-center"
          >
            <h3 class="text-xl font-bold mb-4">ওয়েবসাইট কিউআর কোড</h3>
            <div class="bg-white p-2 rounded-lg mb-4">
              <img :src="qrCodeUrl" alt="Website QR" class="w-40 h-40" />
            </div>
            <p class="text-sm opacity-80">
              স্ক্যান করে বিস্তারিত জানুন এবং প্রচারণা শেয়ার করুন
            </p>
          </div>

          <div class="md:w-2/3 p-8 md:p-12">
            <h2 class="text-3xl font-bold text-green-800 mb-6">
              নির্বাচনী অনুদান
            </h2>
            <p class="text-gray-600 mb-8">
              আপনার সামান্য সহযোগিতা আমাদের সুন্দর আগামীর পথ সুগম করবে। নিচের
              মাধ্যমগুলোতে আপনার অনুদান পাঠাতে পারেন:
            </p>

            <div class="grid grid-cols-1 gap-6">
              <div class="border-b pb-4">
                <h4 class="font-bold text-gray-800">ব্যাংক একাউন্ট</h4>
                <p class="text-sm">একাউন্ট নাম: অ্যাডভোকেট আনিকা নার্গিস</p>
                <p class="text-sm">ব্যাংক: ডাচ-বাংলা ব্যাংক লিমিটেড</p>
                <p class="font-mono text-green-700">২০৩.১৫১.০৯৮৭৬</p>
              </div>

              <div class="grid grid-cols-2 md:grid-cols-4 gap-4 text-center">
                <div
                  class="p-3 border rounded-xl hover:bg-green-50 transition cursor-pointer"
                >
                  <p class="font-bold text-pink-600">bKash</p>
                  <p class="text-xs">01959263946</p>
                </div>
                <div
                  class="p-3 border rounded-xl hover:bg-green-50 transition cursor-pointer"
                >
                  <p class="font-bold text-orange-500">Nagad</p>
                  <p class="text-xs">01959263946</p>
                </div>
                <div
                  class="p-3 border rounded-xl hover:bg-green-50 transition cursor-pointer"
                >
                  <p class="font-bold text-purple-700">Rocket</p>
                  <p class="text-xs">01959263946</p>
                </div>
                <div
                  class="p-3 border rounded-xl hover:bg-green-50 transition cursor-pointer"
                >
                  <p class="font-bold text-blue-500">Upay</p>
                  <p class="text-xs">01959263946</p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <footer class="bg-green-900 text-white pt-12 pb-6">
      <div class="container mx-auto px-4">
        <div class="grid grid-cols-1 md:grid-cols-3 gap-12 items-start mb-8">
          <div class="space-y-4">
            <div class="bg-white p-2 rounded-lg inline-block shadow-lg">
              <img
                src="/images/ncpbd.png"
                alt="Jatiya Nagarik Party Logo"
                class="h-20 w-auto"
              />
            </div>
            <h3 class="text-xl font-bold text-yellow-400">
              জাতীয় নাগরিক পার্টি (NCP)
            </h3>
            <p class="text-gray-300 text-sm leading-relaxed">
              জনগণের উন্নয়ন, জনগণের অগ্রগতি - এটাই আমাদের লক্ষ্য। টাঙ্গাইল-২
              আসনের সুন্দর ভবিষ্যতের জন্য আপনার মূল্যবান ভোট দিয়ে আমাদের পাশে
              থাকুন।
            </p>
          </div>

          <div>
            <h4
              class="text-lg font-bold mb-6 border-b-2 border-yellow-500 pb-2 inline-block"
            >
              লিংকসমূহ
            </h4>
            <ul class="space-y-3">
              <li>
                <a
                  href="#"
                  class="text-gray-300 hover:text-yellow-400 transition"
                  >হোম</a
                >
              </li>
              <li>
                <a
                  href="#about"
                  class="text-gray-300 hover:text-yellow-400 transition"
                  >পরিচিতি</a
                >
              </li>
              <li>
                <a
                  href="#manifesto"
                  class="text-gray-300 hover:text-yellow-400 transition"
                  >নির্বাচনী ইশতেহার</a
                >
              </li>
              <li>
                <a
                  href="#contact"
                  class="text-gray-300 hover:text-yellow-400 transition"
                  >যোগাযোগ</a
                >
              </li>
            </ul>
          </div>

          <div id="contact">
            <h4
              class="text-lg font-bold mb-6 border-b-2 border-yellow-500 pb-2 inline-block"
            >
              যোগাযোগ
            </h4>
            <ul class="space-y-4 text-gray-300 text-sm">
              <li class="flex items-start gap-3">
                <span class="text-yellow-400 text-lg">📍</span>
                <span>নির্বাচনী অফিস, গোপালপুর উপজেলা, ঢাকা</span>
              </li>
              <li class="flex items-center gap-3">
                <span class="text-yellow-400 text-lg">📞</span>
                <span>০১৯৫৯-২৬৩৯৪৬, ০১৭৫৩-১৫২৪০১</span>
              </li>
              <li class="flex items-center gap-3">
                <span class="text-yellow-400 text-lg">✉️</span>
                <span>info@engrnabiladhaka20.com</span>
              </li>
            </ul>
          </div>
        </div>

        <div
          class="border-t border-green-800 mt-12 pt-8 flex flex-col md:flex-row justify-center items-center container mx-auto px-4 text-sm text-gray-400"
        >
          <p class="text-center">
            © {{ currentYear }} অ্যাডভোকেট আনিকা নার্গিস এর প্রচারণা। সর্বস্বত্ব
            সংরক্ষিত।
          </p>
        </div>
      </div>
    </footer>
  </div>
</template>

<style scoped>
@reference "~/assets/main/main.css";
/* Smooth scrolling */
html {
  scroll-behavior: smooth;
}

.stat-card {
  @apply flex flex-col items-center justify-center p-6 border border-green-700 rounded-2xl bg-green-900/50 hover:bg-green-700 transition-colors duration-300;
}
</style>
