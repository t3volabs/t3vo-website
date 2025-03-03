<template>
  <section class="hero-landing">
    <div class="hero-content">
      <span class="pill-badge fade-in-up"> Open Source <span class="sparkle">✨</span> </span>

      <h1 class="hero-title fade-in-up" style="--delay: 0.2s">T3VO</h1>

      <p class="hero-description fade-in-up" style="--delay: 0.3s">
        Your Offline Vault for Passwords, Bookmarks & Private Notes.<br class="hide-mobile" />
        All encrypted. Offline first. Works Everywhere. No Server Needed.
      </p>

      <div class="fade-in-up" style="--delay: 0.4s">
        <a href="https://app.t3vo.com" class="cta-button">
          APP
          <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="arrow-icon">
            <path d="M5 12h14m-7-7 7 7-7 7" />
          </svg>
        </a>
      </div>
    </div>
  </section>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap');

.hero-landing {
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
  background-color: white;
  padding: 2rem;
  font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

.hero-content {
  max-width: 800px;
  text-align: center;
}

.pill-badge {
  display: inline-block;
  background-color: #F5F5F7;
  color: #1D1D1F;
  border-radius: 9999px;
  padding: 0.375rem 1.25rem;
  font-size: 0.875rem;
  font-weight: 500;
  margin-bottom: 2rem;
  letter-spacing: -0.01em;
}

.sparkle {
  margin-left: 0.25rem;
}

.hero-title {
  font-size: 5rem;
  font-weight: 600;
  margin-bottom: 1.5rem;
  color: #1D1D1F;
  letter-spacing: -0.02em;
  line-height: 1.1;
}

.hero-description {
  font-size: 1.5rem;
  line-height: 1.5;
  color: #86868B;
  margin-bottom: 3rem;
  font-weight: 400;
  max-width: 36rem;
  margin-left: auto;
  margin-right: auto;
}

.cta-button {
  display: inline-flex;
  align-items: center;
  background-color: #1D1D1F;
  color: white;
  font-weight: 500;
  padding: 0.875rem 2rem;
  border-radius: 9999px;
  transition: all 0.3s ease;
  text-decoration: none;
}

.cta-button:hover {
  background-color: #2D2D2F;
  transform: translateY(-2px);
}

.arrow-icon {
  margin-left: 0.5rem;
  transition: transform 0.3s ease;
}

.cta-button:hover .arrow-icon {
  transform: translateX(4px);
}

.hide-mobile {
  display: none;
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

@media (min-width: 640px) {
  .hero-title {
    font-size: 6rem;
  }

  .hero-description {
    font-size: 1.75rem;
  }

  .hide-mobile {
    display: inline;
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
