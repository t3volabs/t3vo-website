<template>
    <section class="py-24 relative overflow-hidden">
      <div class="absolute inset-0 bg-gradient-to-r from-blue-50 to-purple-50"></div>
      <div class="relative container mx-auto px-6">
        <h2 class="text-3xl font-bold text-center mb-12">How It Works</h2>
        <div class="grid grid-cols-3 gap-8 items-center max-w-3xl mx-auto">
          <div class="text-center">
            <div class="w-24 h-24 bg-white rounded-2xl shadow-lg mx-auto mb-4 flex items-center justify-center">
              <span class="text-4xl">📱</span>
            </div>
            <p class="font-medium">Your Device</p>
          </div>
          <div class="flex justify-center">
            <svg class="w-full max-w-[200px]" viewBox="0 0 100 10">
              <line x1="0" y1="5" x2="100" y2="5" stroke="currentColor" stroke-width="2" stroke-dasharray="4 2" />
              <polygon points="95,0 95,10 100,5" fill="currentColor" />
            </svg>
          </div>
          <div class="text-center">
            <div class="w-24 h-24 bg-white rounded-2xl shadow-lg mx-auto mb-4 flex items-center justify-center">
              <span class="text-4xl">🔒</span>
            </div>
            <p class="font-medium">Encrypted Storage</p>
          </div>
        </div>
      </div>
    </section>
  </template>