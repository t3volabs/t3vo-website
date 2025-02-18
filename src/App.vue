<template>
  <div class="min-h-screen bg-gradient-to-b from-gray-50 to-white">
    <main>
      <HeroSection />
      <DataFlowDiagram />
      <FeatureComparison />
      <OpenSourceSection />
      <teamSection /> 
    </main>

    <footer class="bg-gray-100 py-8">
      <div class="container mx-auto px-6 text-center text-gray-600">
        <p>&copy; {{ currentYear }} T3VO. All rights reserved.</p>
      </div>
    </footer>
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";
import HeroSection from "./components/HeroSection.vue";
import DataFlowDiagram from "./components/DataFlowDiagram.vue";
import FeatureComparison from "./components/FeaturesC.vue";
import OpenSourceSection from "./components/OpenS.vue";
import teamSection from "./components/team.vue";

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
