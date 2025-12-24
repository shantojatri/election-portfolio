<script setup lang="ts">
import Footer from "./components/Footer.vue";
import Header from "./components/Header.vue";
</script>

<template>
  <NuxtLayout>
    <div class="min-h-screen bg-gray-50 font-sans text-gray-900">
      <!-- Header  -->
      <Header />

      <!-- Main Content  -->
      <main>
        <NuxtPage />
      </main>

      <!-- Footer  -->
      <Footer />
    </div>
  </NuxtLayout>
</template>
