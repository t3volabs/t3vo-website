<template>
  <section id="community" class="py-24 bg-gradient-to-r from-gray-900 to-gray-600 text-white p-12">
    <div class="max-w-4xl mx-auto text-center">
      <div class="inline-block bg-gray-800/50 rounded-full px-4 py-1 text-sm font-medium mb-8">Open Source 💝</div>
      <h2 class="text-4xl font-bold mb-6">Join the T3VO Community</h2>
      <p class="text-gray-300 text-lg mb-12 max-w-2xl mx-auto">T3VO is built by developers for developers. We believe in the power of community-driven development. Fork our repo, add your features, and help us make t3vo even better!</p>

      <div class="grid md:grid-cols-3 gap-8 mb-12">
        <div v-for="feature in communityFeatures" :key="feature.title" class="bg-gray-800/50 rounded-2xl p-6">
          <span class="text-3xl mb-4 block">{{ feature.emoji }}</span>
          <h3 class="font-medium mb-2">{{ feature.title }}</h3>
          <p class="text-gray-400 text-sm">{{ feature.description }}</p>
        </div>
      </div>

      <div class="flex flex-col sm:flex-row gap-4 justify-center">
        <a href="https://github.com/t3volabs" class="inline-flex items-center gap-2 bg-white text-gray-900 font-medium py-3 px-6 rounded-full hover:bg-gray-100 transition transform hover:scale-105">
          <svg viewBox="0 0 24 24" class="w-5 h-5" fill="currentColor">
            <path
              d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"
            />
          </svg>
          Fork on GitHub
        </a>
        <a href="https://github.com/t3volabs/app/issues" class="inline-flex items-center gap-2 bg-gray-800 text-white font-medium py-3 px-6 rounded-full hover:bg-gray-700 transition transform hover:scale-105">
          View Issues
          <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="w-4 h-4">
            <line x1="5" y1="12" x2="19" y2="12"></line>
            <polyline points="12 5 19 12 12 19"></polyline>
          </svg>
        </a>
      </div>
    </div>
  </section>
</template>

<script setup>
const communityFeatures = [
  { emoji: "🔨", title: "Build Features", description: "Add new integrations, enhance security, or improve the UI" },
  { emoji: "🤝", title: "Collaborate", description: "Join discussions, share ideas, and help other developers" },
  { emoji: "🚀", title: "Deploy", description: "Host your own instance with your custom features" },
];
</script>
