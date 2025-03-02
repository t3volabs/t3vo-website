<template>
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
