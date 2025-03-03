<template>
  <section class="min-h-screen bg-white flex items-center py-16 px-4 md:px-8 font-sans antialiased">
    <div class="max-w-7xl mx-auto w-full">
      <!-- Title -->
      <h2 class="text-center text-2xl md:text-4xl font-semibold text-gray-900 mb-12 tracking-tight leading-tight flex flex-col gap-2 animate-fade-in-up">
        Feature Comparison
        <span class="text-gray-400">See how we stack up</span>
      </h2>

      <!-- Table Container -->
      <div 
        class="bg-gradient-to-b from-gray-50 to-white rounded-3xl p-6 md:p-8 shadow-lg overflow-x-auto animate-fade-in-up"
        style="animation-delay: 200ms;"
      >
        <table class="w-full border-separate border-spacing-0 min-w-[800px]">
          <thead>
            <tr>
              <th class="text-left p-6 font-medium text-gray-900 min-w-[200px]">Features</th>
              <th 
                v-for="app in apps" 
                :key="app.name" 
                class="p-6 text-center min-w-[120px]"
              >
                <div class="flex flex-col items-center gap-2 relative">
                  <div class="inline-flex items-center justify-center w-10 h-10 bg-gray-50 rounded-xl">
                    <component :is="app.icon" class="w-5 h-5 text-gray-900" />
                  </div>
                  <span class="font-medium text-gray-900">{{ app.name }}</span>
                  <span 
                    v-if="app.note" 
                    class="text-sm text-blue-600 cursor-help"
                    @mouseenter="showTooltip = app.name"
                    @mouseleave="showTooltip = null"
                  >
                    {{ app.note }}
                    <div 
                      v-if="showTooltip === app.name"
                      class="absolute bottom-full left-1/2 -translate-x-1/2 mb-2 bg-gray-900 text-white px-4 py-3 rounded-xl text-sm whitespace-nowrap z-10 shadow-lg"
                    >
                      That's our app! We've built it with all the essential features you need.
                      <div class="absolute top-full left-1/2 -translate-x-1/2 border-8 border-transparent border-t-gray-900"></div>
                    </div>
                  </span>
                </div>
              </th>
            </tr>
          </thead>
          <tbody>
            <tr 
              v-for="feature in features" 
              :key="feature.feature" 
              class="border-t border-gray-100"
            >
              <td class="p-4 md:p-6 flex items-center gap-3 text-gray-900">
                <component :is="feature.icon" class="w-5 h-5 text-gray-400" />
                <span>{{ feature.feature }}</span>
              </td>
              <td 
                v-for="(supported, index) in feature.apps" 
                :key="index" 
                class="p-4 text-center"
              >
                <div 
                  :class="[
                    'inline-flex items-center justify-center w-8 h-8 rounded-lg',
                    supported ? 'bg-green-100 text-green-700' : 'bg-red-100 text-red-700'
                  ]"
                >
                  <component 
                    :is="supported ? CheckIcon : XIcon"
                    class="w-4 h-4"
                  />
                </div>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'
import { 
  Star, 
  Droplet, 
  Key, 
  Hash, 
  Bookmark, 
  FileText, 
  Tag,
  Lock,
  Wifi,
  Rocket,
  Code,
  DollarSign,
  Shield,
  Zap,
  Check as CheckIcon,
  X as XIcon
} from 'lucide-vue-next'

const showTooltip = ref(null)

const apps = [
  { name: "T3VO", icon: Star, note: "That's us!" },
  { name: "Raindrop", icon: Droplet },
  { name: "LastPass", icon: Key },
  { name: "1Password", icon: Hash },
  { name: "Pocket", icon: Bookmark },
  { name: "Notion", icon: FileText },
  { name: "Pinboard", icon: Tag },
];

const features = [
  { feature: "Password Manager", icon: Lock, apps: [true, false, true, true, false, false, false] },
  { feature: "Bookmark Manager", icon: Bookmark, apps: [true, true, false, false, true, true, true] },
  { feature: "Private Notes", icon: FileText, apps: [true, false, true, true, false, true, false] },
  { feature: "Offline Access", icon: Wifi, apps: [true, false, true, true, false, false, false] },
  { feature: "No Installation Required", icon: Rocket, apps: [true, true, false, false, true, true, true] },
  { feature: "Open Source", icon: Code, apps: [true, false, false, false, false, false, false] },
  { feature: "Free (No Paywalls)", icon: DollarSign, apps: [true, false, false, false, false, false, true] },
  { feature: "End-to-End Encryption", icon: Shield, apps: [true, false, true, true, false, false, false] },
  { feature: "PWA Support", icon: Zap, apps: [true, true, false, false, true, false, false] },
];
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap');

/* Custom animation classes */
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
}

/* Set font family */
.font-sans {
  font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
}
</style>
