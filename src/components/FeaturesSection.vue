<template>
    <section class="features-section">
      <div class="features-container">
        <h2 class="section-title fade-in-up">
          Everything you need
          <span class="text-[#86868B]">for digital security</span>
        </h2>
  
        <div class="features-grid">
          <div 
            v-for="(feature, index) in features" 
            :key="feature.title" 
            class="feature-card fade-in-up"
            :style="{ '--delay': `${0.2 + index * 0.1}s` }"
          >
            <div class="icon-wrapper">
              <component :is="feature.icon" class="feature-icon" />
            </div>
            <h3 class="feature-title">{{ feature.title }}</h3>
            <p class="feature-description">{{ feature.description }}</p>
          </div>
        </div>
      </div>
    </section>
  </template>
  
  <script setup>
  import { 
    Lock, 
    Wifi, 
    Rocket, 
    Bookmark, 
    Key, 
    FileText 
  } from 'lucide-vue-next'
  
  const features = [
    { 
      icon: Lock, 
      title: "End-to-End Encrypted", 
      description: "Your data never leaves your device unencrypted, ensuring maximum privacy and security at all times." 
    },
    { 
      icon: Wifi, 
      title: "Works Offline", 
      description: "Enjoy full functionality without an internet connection, perfect for productivity on-the-go." 
    },
    { 
      icon: Rocket, 
      title: "Zero Install", 
      description: "Use instantly in any modern browser, no downloads or installations required." 
    },
    { 
      icon: Bookmark, 
      title: "Smart Bookmarks", 
      description: "Organize and access your web efficiently with our intelligent bookmarking system." 
    },
    { 
      icon: Key, 
      title: "Password Manager", 
      description: "Keep your credentials secure and easily accessible across all your devices." 
    },
    { 
      icon: FileText, 
      title: "Private Notes", 
      description: "Securely store and sync your thoughts, ideas, and important information." 
    },
  ];
  </script>
  
  <style scoped>
  .features-section {
    min-height: 100vh;
    background-color: white;
    display: flex;
    align-items: center;
    padding: 4rem 2rem;
    font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
  }
  
  .features-container {
    max-width: 1200px;
    margin: 0 auto;
    width: 100%;
  }
  
  .section-title {
    text-align: center;
    font-size: 2.5rem;
    font-weight: 600;
    color: #1D1D1F;
    margin-bottom: 4rem;
    letter-spacing: -0.02em;
    line-height: 1.2;
  }
  
  .features-grid {
    display: grid;
    gap: 2rem;
    grid-template-columns: repeat(1, 1fr);
  }
  
  .feature-card {
    background-color: #F5F5F7;
    border-radius: 1.5rem;
    padding: 2rem;
    transition: all 0.3s ease;
  }
  
  .feature-card:hover {
    transform: translateY(-4px);
    background-color: #EBEBED;
  }
  
  .icon-wrapper {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    width: 3rem;
    height: 3rem;
    background-color: white;
    border-radius: 1rem;
    margin-bottom: 1.5rem;
  }
  
  .feature-icon {
    width: 1.5rem;
    height: 1.5rem;
    color: #1D1D1F;
  }
  
  .feature-title {
    font-size: 1.25rem;
    font-weight: 600;
    color: #1D1D1F;
    margin-bottom: 0.75rem;
    letter-spacing: -0.01em;
  }
  
  .feature-description {
    color: #86868B;
    line-height: 1.6;
    font-size: 1rem;
  }
  
  /* Animation classes */
  .fade-in-up {
    opacity: 0;
    transform: translateY(20px);
    animation: fadeInUp 0.8s ease forwards;
    animation-delay: var(--delay, 0.1s);
  }
  
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
  
  /* Responsive Design */
  @media (min-width: 768px) {
    .features-grid {
      grid-template-columns: repeat(2, 1fr);
    }
    
    .section-title {
      font-size: 3rem;
    }
  }
  
  @media (min-width: 1024px) {
    .features-grid {
      grid-template-columns: repeat(3, 1fr);
    }
  }
  
  /* Reduce motion if user prefers */
  @media (prefers-reduced-motion: reduce) {
    .fade-in-up {
      animation: none;
      opacity: 1;
      transform: translateY(0);
    }
    
    .feature-card:hover {
      transform: none;
    }
  }
  </style>