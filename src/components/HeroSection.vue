<template>
  <div class="font-sans text-gray-900 bg-gradient-to-b from-white to-gray-50">
    <!-- Hero Section -->
    <section class="py-24 text-center max-w-5xl mx-auto px-6">
      <div class="inline-block bg-blue-50 text-blue-600 rounded-full px-4 py-1 text-sm font-medium mb-8 animate-pulse">
        Open Source ✨
      </div>
      <h1 class="text-6xl font-bold mb-6 bg-gradient-to-r from-blue-600 to-purple-600 bg-clip-text text-transparent">
        T 3 V O
      </h1>
      <p class="text-xl text-gray-600 mb-12 leading-relaxed">
        Password manager. Bookmark organizer. Private notes.<br>
        All encrypted. All offline-capable. Zero compromises.
      </p>
      <a href="https://app.t3vo.com" class="inline-flex items-center gap-2 bg-gradient-to-r from-blue-600 to-purple-600 text-white font-medium py-3 px-8 rounded-full hover:from-blue-700 hover:to-purple-700 transition-all duration-300 shadow-lg hover:shadow-xl transform hover:scale-105">
        Get Started – It's Free
        <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
          <path d="M5 12h14m-7-7 7 7-7 7"/>
        </svg>
      </a>
    </section>

    <!-- Features Section -->
    <section id="features" class="py-24">
      <div class="container mx-auto px-6">
        <div class="grid md:grid-cols-3 gap-12 max-w-6xl mx-auto">
          <div v-for="feature in features" :key="feature.title" class="bg-white rounded-3xl p-8 shadow-lg hover:shadow-xl transition-all duration-300 transform hover:-translate-y-1">
            <div class="flex items-center mb-6">
              <span class="text-4xl mr-4">{{ feature.emoji }}</span>
              <h3 class="text-xl font-semibold">{{ feature.title }}</h3>
            </div>
            <p class="text-gray-600 leading-relaxed">{{ feature.description }}</p>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
const features = [
  { emoji: "🔒", title: "End-to-End Encrypted", description: "Your data never leaves your device unencrypted, ensuring maximum privacy and security at all times." },
  { emoji: "📡", title: "Works Offline", description: "Enjoy full functionality without an internet connection, perfect for productivity on-the-go." },
  { emoji: "🚀", title: "Zero Install", description: "Use instantly in any modern browser, no downloads or installations required." },
  { emoji: "🔖", title: "Smart Bookmarks", description: "Organize and access your web efficiently with our intelligent bookmarking system." },
  { emoji: "🎯", title: "Password Manager", description: "Keep your credentials secure and easily accessible across all your devices." },
  { emoji: "📝", title: "Private Notes", description: "Securely store and sync your thoughts, ideas, and important information." },
];
</script>

<style>
 
body {
  font-family: 'Inter', sans-serif;
}

.animate-pulse {
  animation: pulse 2s cubic-bezier(0.4, 0, 0.6, 1) infinite;
}

@keyframes pulse {
  0%, 100% {
    opacity: 1;
  }
  50% {
    opacity: .5;
  }
}
</style>