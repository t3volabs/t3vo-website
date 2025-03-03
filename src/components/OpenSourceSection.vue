<template>
  <section class="community-section">
    <div class="content-wrapper">
      <span 
        class="pill-badge fade-in-up"
      >
        Open Source
        <HeartIcon class="heart-icon" />
      </span>

      <h2 class="section-title fade-in-up" style="--delay: 0.2s">
        Join the T3VO Community
      </h2>

      <p class="section-description fade-in-up" style="--delay: 0.3s">
        T3VO is built by developers for developers. We believe in the power of 
        community-driven development. Fork our repo, add your features, and help 
        us make T3VO even better!
      </p>

      <div class="features-grid">
        <div 
          v-for="(feature, index) in communityFeatures" 
          :key="feature.title"
          class="feature-card fade-in-up"
          :style="{ '--delay': `${0.4 + index * 0.1}s` }"
        >
          <div class="icon-wrapper">
            <component :is="feature.icon" class="feature-icon" />
          </div>
          <h3 class="feature-title">{{ feature.title }}</h3>
          <p class="feature-description">{{ feature.description }}</p>
        </div>
      </div>

      <div class="buttons-wrapper fade-in-up" style="--delay: 0.7s">
        <a 
          href="https://github.com/t3volabs/t3vo-app" 
          class="primary-button"
        >
          <GithubIcon class="button-icon" />
        GitHub
        </a>
        <a 
          href="https://github.com/t3volabs/t3vo-app/issues" 
          class="secondary-button"
        >
          View Issues
          <ArrowRightIcon class="button-icon" />
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

<style scoped>
.community-section {
  min-height: 100vh;
  background: linear-gradient(135deg, #000000, #1D1D1F);
  display: flex;
  align-items: center;
  padding: 4rem 2rem;
  font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: white;
}

.content-wrapper {
  max-width: 1000px;
  margin: 0 auto;
  width: 100%;
  text-align: center;
}

.pill-badge {
  display: inline-flex;
  align-items: center;
  background-color: rgba(255, 255, 255, 0.1);
  border-radius: 9999px;
  padding: 0.5rem 1.25rem;
  font-size: 0.875rem;
  font-weight: 500;
  margin-bottom: 2rem;
  backdrop-filter: blur(10px);
}

.heart-icon {
  width: 1rem;
  height: 1rem;
  margin-left: 0.5rem;
  color: #FF6B6B;
}

.section-title {
  font-size: 3rem;
  font-weight: 600;
  margin-bottom: 1.5rem;
  letter-spacing: -0.02em;
  line-height: 1.2;
}

.section-description {
  font-size: 1.25rem;
  color: rgba(255, 255, 255, 0.8);
  max-width: 36rem;
  margin: 0 auto 3rem;
  line-height: 1.6;
}

.features-grid {
  display: grid;
  gap: 1.5rem;
  margin-bottom: 3rem;
  grid-template-columns: repeat(1, 1fr);
}

.feature-card {
  background-color: rgba(255, 255, 255, 0.1);
  border-radius: 1.25rem;
  padding: 2rem;
  backdrop-filter: blur(10px);
  transition: all 0.3s ease;
}

.feature-card:hover {
  transform: translateY(-4px);
  background-color: rgba(255, 255, 255, 0.15);
}

.icon-wrapper {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 3rem;
  height: 3rem;
  background-color: rgba(255, 255, 255, 0.1);
  border-radius: 1rem;
  margin-bottom: 1.5rem;
}

.feature-icon {
  width: 1.5rem;
  height: 1.5rem;
}

.feature-title {
  font-size: 1.25rem;
  font-weight: 600;
  margin-bottom: 0.75rem;
}

.feature-description {
  color: rgba(255, 255, 255, 0.8);
  font-size: 0.875rem;
  line-height: 1.6;
}

.buttons-wrapper {
  display: flex;
  gap: 1rem;
  justify-content: center;
  flex-direction: column;
  align-items: center;
}

.button-icon {
  width: 1.25rem;
  height: 1.25rem;
}

.primary-button, .secondary-button {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.875rem 1.5rem;
  border-radius: 9999px;
  font-weight: 500;
  transition: all 0.3s ease;
  min-width: 200px;
  justify-content: center;
}

.primary-button {
  background-color: white;
  color: #000000;
}

.primary-button:hover {
  background-color: rgba(255, 255, 255, 0.9);
  transform: translateY(-2px);
}

.secondary-button {
  background-color: rgba(255, 255, 255, 0.1);
  color: white;
}

.secondary-button:hover {
  background-color: rgba(255, 255, 255, 0.15);
  transform: translateY(-2px);
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
@media (min-width: 640px) {
  .buttons-wrapper {
    flex-direction: row;
  }
  
  .section-title {
    font-size: 3.5rem;
  }
}

@media (min-width: 768px) {
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
