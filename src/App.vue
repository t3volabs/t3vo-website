<template>
  <div class="min-h-screen bg-gradient-to-b from-gray-50 to-white">
    <main>
      <HeroSection />
      <FeaturesSection :features="features" />

      <FeatureComparison />
      <OpenSourceSection />
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
import FeatureComparison from "./components/FeaturesC.vue";
import OpenSourceSection from "./components/OpenS.vue";
import FeaturesSection from "./components/FeaturesSection.vue";

const features = [
  { emoji: "🔒", title: "End-to-End Encrypted", description: "Your data never leaves your device unencrypted, ensuring maximum privacy and security at all times." },
  { emoji: "📡", title: "Works Offline", description: "Enjoy full functionality without an internet connection, perfect for productivity on-the-go." },
  { emoji: "🚀", title: "Zero Install", description: "Use instantly in any modern browser, no downloads or installations required." },
  { emoji: "🔖", title: "Smart Bookmarks", description: "Organize and access your web efficiently with our intelligent bookmarking system." },
  { emoji: "🎯", title: "Password Manager", description: "Keep your credentials secure and easily accessible across all your devices." },
  { emoji: "📝", title: "Private Notes", description: "Securely store and sync your thoughts, ideas, and important information." },
];

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
