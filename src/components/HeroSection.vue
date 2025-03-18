<template>
  <section class="flex items-center justify-center min-h-screen bg-white px-4 py-8 font-sans antialiased">
    <div class="max-w-3xl text-center">
      <!-- Badge -->
      <span 
        class="inline-block bg-gray-100 text-gray-900 rounded-full px-5 py-1.5 text-sm font-medium mb-8 animate-fade-in-up"
      >
        Open Source <span class="ml-1">✨</span>
      </span>

      <!-- Title -->
      <h1 
        class="text-5xl md:text-6xl font-semibold mb-6 text-gray-900 leading-tight tracking-tight animate-fade-in-up"
        style="animation-delay: 200ms;"
      >
        T3VO
      </h1>

      <!-- Description -->
      <p 
        class="text-xl md:text-2xl leading-relaxed text-gray-500 mb-12 max-w-2xl mx-auto font-normal animate-fade-in-up"
        style="animation-delay: 300ms;"
      >
        Offline Vault for Passwords, Bookmarks & Private Notes.<br class="hidden sm:inline" />
        All encrypted. Offline first. Works Everywhere. No Server Needed.
      </p>

      <!-- Buttons -->
      <div class="animate-fade-in-up" style="animation-delay: 400ms;">
        <div class="flex flex-wrap justify-center gap-4">
          <a 
            href="https://app.t3vo.com" 
            class="inline-flex items-center bg-gray-900 text-white font-medium px-8 py-3.5 rounded-full transition-all duration-300 hover:bg-gray-800 hover:-translate-y-0.5"
          >
            APP
            <svg 
              xmlns="http://www.w3.org/2000/svg" 
              width="18" 
              height="18" 
              viewBox="0 0 24 24" 
              fill="none" 
              stroke="currentColor" 
              stroke-width="2" 
              stroke-linecap="round" 
              stroke-linejoin="round" 
              class="ml-2 transition-transform duration-300 group-hover:translate-x-1"
            >
              <path d="M5 12h14m-7-7 7 7-7 7" />
            </svg>
          </a>
          
          <a 
            href="https://vercel.com/new/clone?repository-url=https://github.com/t3volabs/t3vo-app/tree/stable" 
            class="inline-flex items-center bg-gray-900 text-white font-medium px-8 py-3.5 rounded-full transition-all duration-300 hover:bg-gray-800 hover:-translate-y-0.5"
          >
            Deploy
            <svg 
              xmlns="http://www.w3.org/2000/svg" 
              width="18" 
              height="18" 
              viewBox="0 0 24 24" 
              fill="none" 
              stroke="currentColor" 
              stroke-width="2" 
              stroke-linecap="round" 
              stroke-linejoin="round" 
              class="ml-2 transition-transform duration-300 group-hover:translate-x-1"
            >
              <path d="M5 12h14m-7-7 7 7-7 7" />
            </svg>
          </a>
        </div>
      </div>
    </div>
  </section>
</template>

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
}

/* Set font family to Inter */
.font-sans {
  font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
}
</style>
