<template>
  <section id="features" class="py-24 bg-gray-50">
    <div class="container mx-auto px-6">
      <div class="grid md:grid-cols-3 gap-8 max-w-4xl mx-auto">
        <div v-for="feature in features" :key="feature.title" class="bg-white rounded-2xl p-6 text-center shadow-lg hover:shadow-xl transition">
          <span class="text-3xl mb-4 block">{{ feature.emoji }}</span>
          <h3 class="font-medium mb-2">{{ feature.title }}</h3>
          <p class="text-sm text-gray-600">{{ feature.description }}</p>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const features = [
  { emoji: "🔒", title: "End-to-End Encrypted", description: "Your data never leaves your device unencrypted" },
  { emoji: "📡", title: "Works Offline", description: "Full functionality without internet connection" },
  { emoji: "🚀", title: "Zero Install", description: "Use instantly in any modern browser" },
  { emoji: "🔖", title: "Smart Bookmarks", description: "Organize and access your web efficiently" },
  { emoji: "🎯", title: "Password Manager", description: "Keep your credentials secure and accessible" },
  { emoji: "📝", title: "Private Notes", description: "Your thoughts, secured and synced" },
];
</script>
