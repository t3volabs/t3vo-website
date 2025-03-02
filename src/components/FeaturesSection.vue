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
  // Define props to receive features data from parent
  import { defineProps } from 'vue';
  
  const props = defineProps({
    features: {
      type: Array,
      required: true
    }
  });
  </script>