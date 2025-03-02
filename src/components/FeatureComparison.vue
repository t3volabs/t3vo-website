<template>
  <section class="comparison-section">
    <div class="content-wrapper">
      <h2 class="section-title fade-in-up">
        Feature Comparison
        <span class="text-[#86868B]">See how we stack up</span>
      </h2>

      <div class="table-container fade-in-up" style="--delay: 0.2s">
        <table class="comparison-table">
          <thead>
            <tr>
              <th class="feature-header">Features</th>
              <th 
                v-for="app in apps" 
                :key="app.name" 
                class="app-header"
              >
                <div class="app-header-content">
                  <div class="icon-wrapper">
                    <component :is="app.icon" class="app-icon" />
                  </div>
                  <span class="app-name">{{ app.name }}</span>
                  <span 
                    v-if="app.note" 
                    class="app-note"
                    @mouseenter="showTooltip = app.name"
                    @mouseleave="showTooltip = null"
                  >
                    {{ app.note }}
                    <div 
                      v-if="showTooltip === app.name"
                      class="tooltip"
                    >
                      That's our app! We've built it with all the essential features you need.
                    </div>
                  </span>
                </div>
              </th>
            </tr>
          </thead>
          <tbody>
            <tr 
              v-for="feature in features" 
              :key="feature.feature" 
              class="feature-row"
            >
              <td class="feature-cell">
                <component :is="feature.icon" class="feature-icon" />
                <span>{{ feature.feature }}</span>
              </td>
              <td 
                v-for="(supported, index) in feature.apps" 
                :key="index" 
                class="status-cell"
              >
                <div 
                  :class="[
                    'status-indicator',
                    supported ? 'status-yes' : 'status-no'
                  ]"
                >
                  <component 
                    :is="supported ? CheckIcon : XIcon"
                    class="status-icon"
                  />
                </div>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'
import { 
  Star, 
  Droplet, 
  Key, 
  Hash, 
  Bookmark, 
  FileText, 
  Tag,
  Lock,
  Wifi,
  Rocket,
  Code,
  DollarSign,
  Shield,
  Zap,
  Check as CheckIcon,
  X as XIcon
} from 'lucide-vue-next'

const showTooltip = ref(null)

const apps = [
  { name: "T3VO", icon: Star, note: "That's us!" },
  { name: "Raindrop", icon: Droplet },
  { name: "LastPass", icon: Key },
  { name: "1Password", icon: Hash },
  { name: "Pocket", icon: Bookmark },
  { name: "Notion", icon: FileText },
  { name: "Pinboard", icon: Tag },
];

const features = [
  { feature: "Password Manager", icon: Lock, apps: [true, false, true, true, false, false, false] },
  { feature: "Bookmark Manager", icon: Bookmark, apps: [true, true, false, false, true, true, true] },
  { feature: "Private Notes", icon: FileText, apps: [true, false, true, true, false, true, false] },
  { feature: "Offline Access", icon: Wifi, apps: [true, false, true, true, false, false, false] },
  { feature: "No Installation Required", icon: Rocket, apps: [true, true, false, false, true, true, true] },
  { feature: "Open Source", icon: Code, apps: [true, false, false, false, false, false, false] },
  { feature: "Free (No Paywalls)", icon: DollarSign, apps: [true, false, false, false, false, false, true] },
  { feature: "End-to-End Encryption", icon: Shield, apps: [true, false, true, true, false, false, false] },
  { feature: "PWA Support", icon: Zap, apps: [true, true, false, false, true, false, false] },
];
</script>

<style scoped>
.comparison-section {
  min-height: 100vh;
  background-color: white;
  display: flex;
  align-items: center;
  padding: 4rem 1rem;
  font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

.content-wrapper {
  max-width: 1200px;
  margin: 0 auto;
  width: 100%;
}

.section-title {
  text-align: center;
  font-size: 2.5rem;
  font-weight: 600;
  color: #1D1D1F;
  margin-bottom: 3rem;
  letter-spacing: -0.02em;
  line-height: 1.2;
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.table-container {
  background: linear-gradient(to bottom, #F5F5F7, white);
  border-radius: 1.5rem;
  padding: 1.5rem;
  box-shadow: 0 4px 40px rgba(0, 0, 0, 0.06);
  overflow-x: auto;
}

.comparison-table {
  width: 100%;
  border-collapse: separate;
  border-spacing: 0;
  min-width: 800px;
}

.feature-header {
  text-align: left;
  padding: 1.5rem;
  font-weight: 500;
  color: #1D1D1F;
  min-width: 200px;
}

.app-header {
  padding: 1.5rem;
  text-align: center;
  min-width: 120px;
}

.app-header-content {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.5rem;
  position: relative;
}

.icon-wrapper {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 2.5rem;
  height: 2.5rem;
  background-color: #F5F5F7;
  border-radius: 0.75rem;
}

.app-icon {
  width: 1.25rem;
  height: 1.25rem;
  color: #1D1D1F;
}

.app-name {
  font-weight: 500;
  color: #1D1D1F;
}

.app-note {
  font-size: 0.875rem;
  color: #0066CC;
  cursor: help;
  position: relative;
}

.tooltip {
  position: absolute;
  bottom: calc(100% + 10px);
  left: 50%;
  transform: translateX(-50%);
  background-color: #1D1D1F;
  color: white;
  padding: 0.75rem 1rem;
  border-radius: 0.75rem;
  font-size: 0.875rem;
  white-space: nowrap;
  z-index: 10;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.2);
}

.tooltip::after {
  content: '';
  position: absolute;
  top: 100%;
  left: 50%;
  transform: translateX(-50%);
  border-width: 6px;
  border-style: solid;
  border-color: #1D1D1F transparent transparent transparent;
}

.feature-row {
  border-top: 1px solid #F5F5F7;
}

.feature-cell {
  padding: 1rem 1.5rem;
  display: flex;
  align-items: center;
  gap: 0.75rem;
  color: #1D1D1F;
}

.feature-icon {
  width: 1.25rem;
  height: 1.25rem;
  color: #86868B;
}

.status-cell {
  padding: 1rem;
  text-align: center;
}

.status-indicator {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 2rem;
  height: 2rem;
  border-radius: 0.5rem;
}

.status-yes {
  background-color: #E8F5E9;
  color: #2E7D32;
}

.status-no {
  background-color: #FFEBEE;
  color: #C62828;
}

.status-icon {
  width: 1rem;
  height: 1rem;
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
  .comparison-section {
    padding: 4rem 2rem;
  }
  
  .section-title {
    font-size: 3rem;
  }
  
  .table-container {
    padding: 2rem;
  }
}

/* Reduce motion if user prefers */
@media (prefers-reduced-motion: reduce) {
  .fade-in-up {
    animation: none;
    opacity: 1;
    transform: translateY(0);
  }
}
</style>