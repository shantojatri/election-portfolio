<script setup lang="ts">
import { ref } from "vue";

const isSubmitting = ref(false);
const isSuccess = ref(false);

const formData = ref({
  name: "",
  phone: "",
  location: "",
  address: "",
  reason: "",
});

// আপনার Google Apps Script URL এখানে বসাবেন
const GOOGLE_SCRIPT_URL =
  "https://script.google.com/macros/s/AKfycbzBq0nellUFGnSdyPGTyrLXdCsFWFHJ7kjAVclqAvNDOhBSaSjdJ41p3s1cDL_RL--EIw/exec";

const submitForm = async () => {
  isSubmitting.value = true;

  try {
    // Google Sheet এ ডেটা পাঠানোর লজিক
    await fetch(GOOGLE_SCRIPT_URL, {
      method: "POST",
      mode: "no-cors", // Google Script এর জন্য জরুরি
      headers: { "Content-Type": "application/json" },
      body: JSON.stringify(formData.value),
    });

    isSuccess.value = true;
    formData.value = {
      name: "",
      phone: "",
      location: "",
      address: "",
      reason: "",
    };
  } catch (error) {
    alert("দুঃখিত, কোনো সমস্যা হয়েছে। আবার চেষ্টা করুন।");
  } finally {
    isSubmitting.value = false;
  }
};
</script>

<template>
  <header class="bg-green-800 text-white py-12 text-center">
    <h1 class="text-3xl md:text-4xl font-black mb-2">
      স্বেচ্ছাসেবক হিসেবে যোগ দিন
    </h1>
    <p class="text-yellow-400">আপনার দক্ষতাই হবে আমাদের আগামীর শক্তি</p>
  </header>

  <main class="flex-grow container mx-auto px-4 py-12">
    <div
      class="max-w-2xl mx-auto bg-white rounded-3xl shadow-2xl overflow-hidden border border-gray-100"
    >
      <div v-if="isSuccess" class="p-12 text-center animate-fade-in">
        <div class="text-6xl mb-4">🎉</div>
        <h2 class="text-2xl font-bold text-green-700 mb-2">আবেদন সফল হয়েছে!</h2>
        <p class="text-gray-600">
          আমরা শীঘ্রই আপনার সাথে যোগাযোগ করব। আমাদের সাথে থাকার জন্য ধন্যবাদ।
        </p>
        <button
          @click="isSuccess = false"
          class="mt-6 text-green-700 font-bold underline"
        >
          আরেকটি আবেদন করুন
        </button>
      </div>

      <form v-else @submit.prevent="submitForm" class="p-8 md:p-12 space-y-6">
        <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
          <div>
            <label class="block text-sm font-bold text-gray-700 mb-2"
              >পূর্ণ নাম</label
            >
            <input
              v-model="formData.name"
              type="text"
              required
              placeholder="আপনার নাম"
              class="form-input"
            />
          </div>
          <div>
            <label class="block text-sm font-bold text-gray-700 mb-2"
              >মোবাইল নম্বর</label
            >
            <input
              v-model="formData.phone"
              type="tel"
              required
              placeholder="০১XXX-XXXXXX"
              class="form-input"
            />
          </div>
        </div>

        <div>
          <label class="block text-sm font-bold text-gray-700 mb-2"
            >পৌরসভা / ইউনিয়ন</label
          >
          <input
            v-model="formData.location"
            type="text"
            required
            placeholder="উদা: গোপালপুর পৌরসভা"
            class="form-input"
          />
        </div>

        <div>
          <label class="block text-sm font-bold text-gray-700 mb-2"
            >বিস্তারিত ঠিকানা</label
          >
          <textarea
            v-model="formData.address"
            required
            rows="2"
            placeholder="গ্রাম, পোস্ট অফিস ইত্যাদি"
            class="form-input"
          ></textarea>
        </div>

        <div>
          <label class="block text-sm font-bold text-gray-700 mb-2"
            >কেন স্বেচ্ছাসেবক হতে চান?</label
          >
          <textarea
            v-model="formData.reason"
            required
            rows="4"
            placeholder="আপনার লক্ষ্য বা উদ্দেশ্য সংক্ষেপে লিখুন..."
            class="form-input"
          ></textarea>
        </div>

        <button
          type="submit"
          :disabled="isSubmitting"
          class="w-full bg-green-700 text-white font-bold py-4 rounded-xl hover:bg-green-800 transition-all shadow-lg flex items-center justify-center gap-2"
        >
          <span
            v-if="isSubmitting"
            class="animate-spin border-2 border-white border-t-transparent rounded-full w-5 h-5"
          ></span>
          {{ isSubmitting ? "প্রসেসিং হচ্ছে..." : "আবেদন জমা দিন" }}
        </button>
      </form>
    </div>
  </main>
</template>

<style scoped>
@reference "~/assets/main/main.css";
.form-input {
  @apply w-full p-4 bg-gray-50 border border-gray-200 rounded-xl focus:ring-2 focus:ring-green-500 focus:bg-white outline-none transition-all;
}
.animate-fade-in {
  animation: fadeIn 0.5s ease-out;
}
@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(10px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>
