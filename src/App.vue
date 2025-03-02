<template>
  <div class="min-h-screen">
    <main>
      <HeroSection />

      <FeaturesSection />

      <FeatureComparison />

      <OpenSourceSection />
    </main>

    <footer class="py-8">
      <div class="container mx-auto px-6 text-center text-gray-600">
        <p>&copy; {{ currentYear }} T3VO. All rights reserved.</p>
      </div>
    </footer>
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";
import HeroSection from "./components/HeroSection.vue";
import FeatureComparison from "./components/FeatureComparison.vue";
import OpenSourceSection from "./components/OpenSourceSection.vue";
import FeaturesSection from "./components/FeaturesSection.vue";

const currentYear = ref(new Date().getFullYear());
</script>

<style>
html {
  scroll-behavior: smooth;
}

@keyframes float {
  0% {
    transform: translateY(0px);
  }
  50% {
    transform: translateY(-20px);
  }
  100% {
    transform: translateY(0px);
  }
}

.float-animation {
  animation: float 6s ease-in-out infinite;
}
</style>
