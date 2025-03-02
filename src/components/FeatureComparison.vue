<template>
  <section id="comparison" class="py-24 bg-white">
    <div class="container mx-auto px-6">
      <div class="w-full bg-gradient-to-b from-gray-50 to-white rounded-3xl p-4 md:p-8 shadow-lg overflow-x-auto">
        <table class="w-full table-auto">
          <thead>
            <tr class="border-b border-gray-100">
              <th class="py-2 px-2 md:py-4 md:px-6 text-left min-w-[200px]">Features</th>
              <th v-for="app in apps" :key="app.name" class="py-2 px-2 md:py-4 md:px-6 text-center">
                <div class="flex flex-col items-center">
                  <span class="text-2xl mb-2">{{ app.emoji }}</span>
                  <span class="font-medium">{{ app.name }}</span>
                  <span v-if="app.note" class="text-sm text-blue-600">{{ app.note }}</span>
                </div>
              </th>
            </tr>
          </thead>
          <tbody class="text-sm">
            <tr v-for="feature in features" :key="feature.feature" class="border-b border-gray-50 hover:bg-gray-50 transition-colors">
              <td class="py-2 px-2 md:py-4 md:px-6 flex items-center gap-2">
                <span>{{ feature.emoji }}</span>
                <span>{{ feature.feature }}</span>
              </td>
              <td v-for="(supported, index) in feature.apps" :key="index" class="py-2 px-2 md:py-4 md:px-6 text-center">
                <span :class="['inline-flex items-center justify-center w-6 h-6 rounded-full', supported ? 'bg-green-100 text-green-600' : 'bg-red-100 text-red-600']">
                  {{ supported ? "✓" : "×" }}
                </span>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </section>
</template>

<script setup>
const apps = [
  { name: "T3VO", emoji: "⭐️", note: "That's us!" },
  { name: "Raindrop", emoji: "💧" },
  { name: "LastPass", emoji: "🔑" },
  { name: "1Password", emoji: "1️⃣" },
  { name: "Pocket", emoji: "🌟" },
  { name: "Notion", emoji: "📝" },
  { name: "Pinboard", emoji: "🔖" },
];

const features = [
  { feature: "Password Manager", emoji: "🔐", apps: [true, false, true, true, false, false, false] },
  { feature: "Bookmark Manager", emoji: "🔖", apps: [true, true, false, false, true, true, true] },
  { feature: "Private Notes", emoji: "📝", apps: [true, false, true, true, false, true, false] },
  { feature: "Offline Access", emoji: "📡", apps: [true, false, true, true, false, false, false] },
  { feature: "No Installation Required", emoji: "🚀", apps: [true, true, false, false, true, true, true] },
  { feature: "Open Source", emoji: "💻", apps: [true, false, false, false, false, false, false] },
  { feature: "Free (No Paywalls)", emoji: "💰", apps: [true, false, false, false, false, false, true] },
  { feature: "End-to-End Encryption", emoji: "🔒", apps: [true, false, true, true, false, false, false] },
  { feature: "PWA Support", emoji: "⚡️", apps: [true, true, false, false, true, false, false] },
];
</script>
