<template>
  <section class="min-h-screen bg-gradient-to-br from-black to-gray-900 flex items-center py-16 px-4 md:px-8 font-sans text-white antialiased">
    <div class="max-w-5xl mx-auto w-full text-center">
      <!-- Badge -->
      <span 
        class="inline-flex items-center bg-white/10 backdrop-blur-lg rounded-full px-5 py-2 text-sm font-medium mb-8 animate-fade-in-up"
      >
        Open Source
        <HeartIcon class="w-4 h-4 ml-2 text-red-400" />
      </span>

      <!-- Title & Description -->
      <h2 
        class="text-3xl md:text-4xl lg:text-5xl font-semibold mb-6 tracking-tight leading-tight animate-fade-in-up"
        style="animation-delay: 200ms;"
      >
        Join the T3VO Community
      </h2>

      <p 
        class="text-lg md:text-xl text-white/80 max-w-2xl mx-auto mb-12 leading-relaxed animate-fade-in-up"
        style="animation-delay: 300ms;"
      >
        T3VO is built by developers for developers. We believe in the power of 
        community-driven development. Fork our repo, add your features, and help 
        us make T3VO even better!
      </p>

      <!-- Features Grid -->
      <div class="grid gap-6 grid-cols-1 md:grid-cols-3 mb-12">
        <div 
          v-for="(feature, index) in communityFeatures" 
          :key="feature.title"
          class="bg-white/10 backdrop-blur-lg rounded-2xl p-8 transition-all duration-300 hover:-translate-y-1 hover:bg-white/15 animate-fade-in-up"
          :style="{ 'animation-delay': `${0.4 + index * 0.1}s` }"
        >
          <div class="inline-flex items-center justify-center w-12 h-12 bg-white/10 rounded-2xl mb-6">
            <component :is="feature.icon" class="w-6 h-6" />
          </div>
          <h3 class="text-xl font-semibold mb-3">{{ feature.title }}</h3>
          <p class="text-white/80 text-sm leading-relaxed">{{ feature.description }}</p>
        </div>
      </div>

      <!-- Buttons -->
      <div 
        class="flex flex-col sm:flex-row gap-4 justify-center items-center animate-fade-in-up"
        style="animation-delay: 700ms;"
      >
        <a 
          href="https://github.com/t3volabs/t3vo-app" 
          class="inline-flex items-center justify-center gap-2 bg-white text-black min-w-[200px] px-6 py-3.5 rounded-full font-medium transition-all duration-300 hover:-translate-y-0.5 hover:bg-white/90"
        >
          <GithubIcon class="w-5 h-5" />
          GitHub
        </a>
        <a 
          href="https://github.com/t3volabs/t3vo-app/issues" 
          class="inline-flex items-center justify-center gap-2 bg-white/10 text-white min-w-[200px] px-6 py-3.5 rounded-full font-medium transition-all duration-300 hover:-translate-y-0.5 hover:bg-white/15"
        >
          View Issues
          <ArrowRightIcon class="w-5 h-5" />
        </a>
      </div>
    </div>
  </section>
</template>

<script setup>
import { 
  Github as GithubIcon,
  Heart as HeartIcon,
  ArrowRight as ArrowRightIcon,
  Hammer as HammerIcon,
  Users as UsersIcon,
  Rocket as RocketIcon
} from 'lucide-vue-next'

const communityFeatures = [
  { 
    icon: HammerIcon,
    title: "Build Features", 
    description: "Add new integrations, enhance security, or improve the UI" 
  },
  { 
    icon: UsersIcon,
    title: "Collaborate", 
    description: "Join discussions, share ideas, and help other developers" 
  },
  { 
    icon: RocketIcon,
    title: "Deploy", 
    description: "Host your own instance with your custom features" 
  },
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
  
  .hover\:-translate-y-1:hover,
  .hover\:-translate-y-0\.5:hover {
    transform: none;
  }
}

/* Set font family */
.font-sans {
  font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
}
</style>
