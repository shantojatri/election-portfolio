<script setup>
import { ref } from "vue";

const currentYear = new Date().getFullYear();

// সংস্কারের ডাটা স্ট্রাকচার
const reformCategories = [
  {
    title: "১. নির্বাচন ও নিয়োগ সংক্রান্ত",
    data: [
      {
        subject: "নির্বাচন কমিশন নিয়োগ",
        current: "আইন থাকলেও নিয়োগ হয় প্রধানমন্ত্রীর মাধ্যমে।",
        proposal:
          "স্পিকার, বিরোধী দল থেকে নির্বাচিত ডেপুটি স্পিকার, প্রধানমন্ত্রী, বিরোধী দলীয় নেতা ও আপিল বিভাগ প্রভৃতির সমন্বিত কমিটির মাধ্যমে নিয়োগ।",
      },
      {
        subject: "পিএসসি নিয়োগ",
        current: "পিএসসিতে নিয়োগ দেন প্রধানমন্ত্রী।",
        proposal:
          "স্পিকার ও চিফ হুইপ, বিরোধী দল থেকে নির্বাচিত ডেপুটি স্পিকার ও চিফ হুইপ, বিরোধীদলীয় প্রতিনিধি প্রভৃতির সমন্বিত কমিটির মাধ্যমে পিএসসিতে নিয়োগ।",
      },
      {
        subject: "মহা-হিসাব নিরীক্ষক",
        current: "নিয়োগ দেন প্রধানমন্ত্রী।",
        proposal:
          "বিরোধী দল থেকে নির্বাচিত ডেপুটি স্পিকার, সরকারি দলের নেতা, বিরোধী দলীয় নেতা প্রভৃতির সমন্বিত কমিটির মাধ্যমে নিয়োগ।",
      },
      {
        subject: "দুদক নিয়োগ",
        current:
          "দুদক চেয়ারম্যান ও কমিশনার নিয়োগ প্রধানমন্ত্রীর নিয়ন্ত্রণে।",
        proposal:
          "দুদককে সাংবিধানিক মর্যাদা দেওয়া এবং সরকার ও বিরোধী দলের প্রতিনিধি প্রভৃতির সমন্বিত কমিটির মাধ্যমে নিয়োগ।",
      },
      {
        subject: "মামলায় অনুমোদন",
        current: "সরকারি কর্মচারীদের বিরুদ্ধে মামলা করতে সরকারের অনুমোদন লাগে।",
        proposal:
          "সরকারি কর্মচারীদের বিরুদ্ধে মামলা করতে সরকারের অনুমোদন লাগবে না (দুদকের ক্ষেত্রে)।",
      },
    ],
  },
  {
    title: "২. বিচার বিভাগ সংক্রান্ত",
    data: [
      {
        subject: "প্রধান বিচারপতি নিয়োগ",
        current: "রাষ্ট্রপতি যে কাউকেও প্রধান বিচারপতি নিয়োগ করতে পারেন।",
        proposal: "আপিল বিভাগ থেকে প্রধান বিচারপতি নিয়োগ।",
      },
      {
        subject: "হাইকোর্টের বিচারক নিয়োগ",
        current: "নিয়োগ প্রধানমন্ত্রীর নিয়ন্ত্রণে।",
        proposal:
          "প্রধান বিচারপতির নেতৃত্বাধীন কমিশনের মাধ্যমে হাইকোর্টের বিচারক নিয়োগ।",
      },
      {
        subject: "নিয়োগ কমিশন",
        current: "বিচারক নিয়োগ কমিশনের বিধান সংবিধানে নেই।",
        proposal: "বিধান সংবিধানে অন্তর্ভুক্ত হবে।",
      },
      {
        subject: "আদালতের অবস্থান",
        current: "আপিল বিভাগ ও হাইকোর্ট শুধু ঢাকায়।",
        proposal: "প্রত্যেক বিভাগে হাইকোর্টের এক বা একাধিক বেঞ্চ স্থাপন।",
      },
      {
        subject: "স্বাধীনতা",
        current: "বিচার বিভাগের পূর্ণ স্বাধীনতা নেই।",
        proposal: "বিচার বিভাগকে পূর্ণ স্বাধীনতার সাংবিধানিক নিশ্চয়তা।",
      },
    ],
  },
  {
    title: "৩. সংসদ ও শাসনব্যবস্থা",
    data: [
      {
        subject: "তত্ত্বাবধায়ক সরকার",
        current: "সংবিধানে এই ব্যবস্থা নেই।",
        proposal: "তত্ত্বাবধায়ক সরকার ব্যবস্থার প্রত্যাবর্তন।",
      },
      {
        subject: "সংসদীয় আসন",
        current: "বর্তমানে সংসদে পিআর (PR) পদ্ধতি নেই।",
        proposal:
          "উচ্চকক্ষে পিআর (Proportional Representation) পদ্ধতিতে আসন বণ্টন হবে।",
      },
      {
        subject: "ডেপুটি স্পিকার",
        current: "সরকারি দল থেকে নির্বাচিত হন।",
        proposal: "ডেপুটি স্পিকার বাধ্যতামূলকভাবে বিরোধী দল থেকে হবেন।",
      },
      {
        subject: "এমপিদের ভোট",
        current: "দলীয় সিদ্ধান্তের বাইরে ভোট দিলে সদস্য পদ বাতিল।",
        proposal:
          "বাজেট ও আস্থা বিল ছাড়া অন্য সব বিষয়ে এমপিরা স্বাধীনভাবে ভোট দিতে পারবেন।",
      },
      {
        subject: "বিদেশি চুক্তি",
        current: "বিদেশের সঙ্গে চুক্তিতে সংসদের অনুমোদনের প্রয়োজন নেই।",
        proposal:
          "রাষ্ট্রীয় নিরাপত্তা-সংক্রান্ত চুক্তিতে সংসদের উভয় কক্ষের অনুমোদন লাগবে।",
      },
      {
        subject: "সংসদীয় কাঠামো",
        current: "বর্তমান সংসদ এক-কক্ষবিশিষ্ট।",
        proposal: "সংসদ হবে দ্বি-কক্ষবিশিষ্ট, যেখানে উচ্চকক্ষে থাকবে ১০০ আসন।",
      },
    ],
  },
  {
    title: "৪. ক্ষমতা ও সংবিধান",
    data: [
      {
        subject: "প্রধানমন্ত্রীর মেয়াদ",
        current: "এক ব্যক্তি যত বছর ইচ্ছা পদে থাকতে পারেন।",
        proposal:
          "এক ব্যক্তি পুরো জীবনে ১০ বছরের বেশি প্রধানমন্ত্রী পদে থাকতে পারবেন না।",
      },
      {
        subject: "জরুরি অবস্থা",
        current: "প্রধানমন্ত্রীর জরুরি অবস্থা জারির ক্ষমতা।",
        proposal: "মন্ত্রিসভার অনুমোদন লাগবে, যেখানে বিরোধীদলীয় নেতাও থাকবেন।",
      },
      {
        subject: "সংবিধান সংশোধন",
        current: "দুই-তৃতীয়াংশ সংখ্যাগরিষ্ঠতা লাগে, গণভোট লাগে না।",
        proposal:
          "নিম্নকক্ষে দুই-তৃতীয়াংশ এবং উচ্চকক্ষে সংখ্যাগরিষ্ঠতা লাগবে। তত্ত্বাবধায়ক ব্যবস্থাসহ কয়েকটিতে গণভোট লাগবে।",
      },
      {
        subject: "ভাষার স্বীকৃতি",
        current: "বাংলা ছাড়া অন্য ভাষার স্বীকৃতি নেই।",
        proposal:
          "রাষ্ট্রভাষা হবে বাংলা। অন্য সব মাতৃভাষাকেও স্বীকৃতি দেওয়া হবে।",
      },
      {
        subject: "অনুচ্ছেদ ৭ক ও ৭খ",
        current: "সংবিধান রহিত করলে সর্বোচ্চ শাস্তির বিধান।",
        proposal: "এই অনুচ্ছেদগুলোর বিলোপ।",
      },
    ],
  },
  {
    title: "৫. রাষ্ট্রপতি ও অন্যান্য সংস্কার",
    data: [
      {
        subject: "রাষ্ট্রপতির ক্ষমতা",
        current: "কেবল প্রধানমন্ত্রী ও বিচারপতি নিয়োগ দিতে পারেন।",
        proposal:
          "প্রধানমন্ত্রীর পরামর্শ ছাড়াই ব্যাংকের গভর্নর, প্রেস কাউন্সিল, তথ্য কমিশন ও আইন কমিশনের চেয়ারম্যান নিয়োগ দিতে পারবেন।",
      },
      {
        subject: "ক্ষমা প্রদর্শন",
        current: "সরকারের অনুরোধে যে কাউকেও ক্ষমা করতে পারেন।",
        proposal:
          "ক্ষতিগ্রস্ত পরিবারের সম্মতিতে অপরাধীকে ক্ষমা করতে পারবেন রাষ্ট্রপতি।",
      },
      {
        subject: "স্থানীয় নির্বাচন",
        current: "সরকারের অনুরোধে ইসি আয়োজন করে।",
        proposal: "স্থানীয় নির্বাচনের দায়িত্ব সাংবিধানিকভাবে ইসিকে দেওয়া।",
      },
      {
        subject: "সম্পদের হিসাব",
        current: "জনপ্রতিনিধিরা শুধু নির্বাচনের সময় হিসাব দেন।",
        proposal:
          "জনপ্রতিনিধিরা প্রতিবছর সম্পদের হিসাব দেবেন, যা ওয়েবসাইটে থাকবে।",
      },
      {
        subject: "আইনজীবী সংগঠন",
        current: "সরাসরি দলীয় রাজনীতিতে যুক্ত।",
        proposal: "আইনজীবী সংগঠন দলীয় রাজনীতির বাইরে থাকা।",
      },
      {
        subject: "প্রশাসনিক বিভাগ",
        current: "বর্তমানে ৮টি বিভাগ আছে।",
        proposal: "কুমিল্লা ও ফরিদপুর বিভাগ করা।",
      },
      {
        subject: "কালো টাকা",
        current: "সাদা করার সুযোগ আছে।",
        proposal: "কালো টাকা সাদা করার সুযোগ চিরতরে বন্ধের আইন।",
      },
      {
        subject: "বেসরকারি দুর্নীতি",
        current: "বেসরকারি প্রতিষ্ঠানের দুর্নীতি দুদকের আওতাভুক্ত নয়।",
        proposal:
          "বেসরকারি প্রতিষ্ঠানের আর্থিক অপরাধ ও দুর্নীতিকে দুদকের আওতায় আনা।",
      },
      {
        subject: "পুলিশ কমিশন",
        current: "স্বাধীন পুলিশ কমিশন নেই।",
        proposal:
          "বিচারপতি, সংসদ নেতা ও বিরোধী দলীয় নেতা প্রভৃতির সমন্বয়ে স্বাধীন পুলিশ কমিশন গঠন।",
      },
    ],
  },
];
</script>

<template>
  <header class="bg-green-800 text-white py-12 md:py-16 text-center">
    <div class="container mx-auto px-4">
      <h2 class="text-3xl md:text-5xl font-black mb-4">
        জুলাই সনদ: প্রস্তাবিত সংস্কারসমূহ
      </h2>

      <p class="text-yellow-400 text-base md:text-lg max-w-2xl mx-auto mb-4">
        ফ্যাসিবাদী ব্যবস্থার বিলোপ এবং একটি গণতান্ত্রিক ও বৈষম্যহীন নতুন
        বাংলাদেশ গড়ার রোডম্যাপ।
      </p>
      <h3 class="text-2xl md:text-3xl font-black">
        ✅ গণ ভোটে হ্যাঁ জয়যুক্ত হলে বাস্তবায়ন করা হবে নিচের সংস্কার গুলো
      </h3>
    </div>
  </header>

  <section class="container mx-auto px-4 mt-8 space-y-10 pb-12">
    <div
      v-for="category in reformCategories"
      :key="category.title"
      class="bg-white rounded-2xl shadow-lg overflow-hidden border border-gray-200 mb-6"
    >
      <div class="bg-green-700 px-5 py-3">
        <h3 class="text-lg md:text-xl font-bold text-yellow-400">
          {{ category.title }}
        </h3>
      </div>

      <div class="overflow-x-auto">
        <table class="w-full text-left border-collapse border-hidden">
          <thead>
            <tr class="bg-green-50 text-green-900">
              <th
                class="table-cell font-bold uppercase text-xs md:text-sm w-1/4 border border-gray-200"
              >
                বিষয়
              </th>
              <th
                class="table-cell font-bold uppercase text-xs md:text-sm w-1/3 border border-gray-200"
              >
                এখন আছে
              </th>
              <th
                class="table-cell font-bold uppercase text-xs md:text-sm w-1/3 text-green-700 border border-gray-200"
              >
                চূড়ান্ত প্রস্তাব
              </th>
            </tr>
          </thead>
          <tbody>
            <tr
              v-for="(item, idx) in category.data"
              :key="idx"
              class="hover:bg-gray-50 transition-colors"
            >
              <td
                class="table-cell font-bold text-gray-800 border border-gray-100"
              >
                {{ item.subject }}
              </td>
              <td
                class="table-cell text-gray-600 text-xs md:text-sm border border-gray-100"
              >
                {{ item.current }}
              </td>
              <td
                class="table-cell text-green-800 font-medium text-xs md:text-sm bg-green-50/20 border border-gray-100"
              >
                {{ item.proposal }}
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </section>
</template>

<style scoped>
@reference "~/assets/main/main.css";

/* প্যাডিং কমানোর জন্য কাস্টম ক্লাস */
.table-cell {
  @apply p-3 md:p-4 leading-tight align-top;
}

/* টেবিল বর্ডার ফিক্স */
table {
  border-spacing: 0;
  width: 100%;
}

.overflow-x-auto {
  -webkit-overflow-scrolling: touch;
}
</style>
