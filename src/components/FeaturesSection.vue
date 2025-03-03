<template>
  <section class="min-h-screen bg-gradient-to-br from-black to-gray-900 flex items-center py-16 px-4 md:px-8 font-sans text-white antialiased">
    <div class="max-w-7xl mx-auto w-full">
      <h2 class="text-center text-2xl md:text-3xl lg:text-4xl font-semibold mb-16 tracking-tight leading-tight animate-fade-in-up">
        Everything you need
        <span class="text-gray-400">for digital security</span>
      </h2>

      <div class="grid gap-8 grid-cols-1 md:grid-cols-2 lg:grid-cols-3">
        <div 
          v-for="(feature, index) in features" 
          :key="feature.title" 
          class="bg-white/5 backdrop-blur-lg rounded-3xl p-8 transition-all duration-300 hover:-translate-y-1 hover:bg-white/8 border border-white/10 hover:border-white/20 animate-fade-in-up"
          :style="{ 'animation-delay': `${0.2 + index * 0.1}s` }"
        >
          <div class="inline-flex items-center justify-center w-12 h-12 bg-white/10 rounded-2xl mb-6">
            <component :is="feature.icon" class="w-6 h-6 text-white" />
          </div>
          <h3 class="text-xl font-semibold text-white mb-3 tracking-tight">{{ feature.title }}</h3>
          <p class="text-white/70 leading-relaxed">{{ feature.description }}</p>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { Lock, Wifi, Rocket, Bookmark, Key, FileText, UserRoundPen, Pyramid } from "lucide-vue-next";

const features = [
  {
    icon: Lock,
    title: "End-to-End Encrypted",
    description: "Your data never leaves your device unencrypted, ensuring maximum privacy and security at all times.",
  },
  {
    icon: UserRoundPen,
    title: "Unlmitied Storage & Profiles",
    description: "Create and manage multiple profiles for different use cases, unlimited storage for all.",
  },
  {
    icon: Wifi,
    title: "Works Offline",
    description: "Enjoy full functionality without an internet connection, perfect for productivity on-the-go.",
  },
  {
    icon: Rocket,
    title: "Zero Install",
    description: "Use instantly in any modern browser, no downloads or installations required.",
  },
  {
    icon: Bookmark,
    title: "Smart Bookmarks",
    description: "Organize and access your web efficiently with our intelligent bookmarking system.",
  },
  {
    icon: Key,
    title: "Password Manager",
    description: "Keep your credentials secure and easily accessible across all your devices.",
  },
  {
    icon: FileText,
    title: "Private Notes",
    description: "Securely store and sync your thoughts, ideas, and important information.",
  },
  {
    icon: Pyramid,
    title: "Client First Design",
    description: "No server required, all data is stored on your device and encrypted with your keys.",
  },
];
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap');

/* Custom animation classes that aren't available in default Tailwind */
@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.animate-fade-in-up {
  opacity: 0;
  transform: translateY(20px);
  animation: fadeInUp 0.8s ease forwards;
}

/* Respect user preferences for reduced motion */
@media (prefers-reduced-motion: reduce) {
  .animate-fade-in-up {
    animation: none;
    opacity: 1;
    transform: translateY(0);
  }
  
  .hover\:-translate-y-1:hover {
    transform: none;
  }
}

/* Set font family to Inter */
.font-sans {
  font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
}
</style>
