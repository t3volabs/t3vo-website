<template>
  <section class="py-16 bg-gradient-to-b from-gray-50 to-white">
    <div class="container mx-auto px-4">
      <div class="text-center mb-16">
        <h2 class="text-4xl font-bold text-gray-900 mb-4">Meet Our Team</h2>
        <p class="text-xl text-gray-600 max-w-2xl mx-auto">At T3VO Labs, our diverse team of passionate developers is dedicated to pushing the boundaries of technology. Together, we're building the future of web development.</p>
      </div>

      <div class="mb-12">
        <div class="flex justify-between items-center mb-8">
          <h3 class="text-2xl font-semibold text-gray-800">Top Contributors</h3>
          <a href="https://github.com/t3volabs" target="_blank" rel="noopener noreferrer" class="text-blue-600 hover:text-blue-800 transition duration-300"> View All on GitHub → </a>
        </div>

        <div v-if="loading" class="flex justify-center items-center h-64">
          <div class="w-12 h-12 border-4 border-blue-500 border-t-transparent rounded-full animate-spin"></div>
        </div>

        <div v-else-if="error" class="text-center text-red-500 p-4">
          {{ error }}
        </div>

        <div v-else class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 lg:grid-cols-5 gap-6">
          <div v-for="contributor in contributors" :key="contributor.id" class="contributor-card bg-white rounded-lg shadow-md overflow-hidden transition-all duration-300 ease-in-out hover:shadow-xl" :class="{ expanded: expandedCard === contributor.id }" @mouseenter="expandedCard = contributor.id" @mouseleave="expandedCard = null">
            <div class="relative pb-[100%]">
              <img :src="contributor.avatar_url" :alt="contributor.login" class="absolute h-full w-full object-cover" />
            </div>
            <div class="p-4">
              <h4 class="text-lg font-medium text-gray-900 truncate mb-2">{{ contributor.login }}</h4>
              <div class="flex justify-between text-sm text-gray-600 mb-3">
                <span>{{ contributor.totalCommits }} commits</span>
                <span>{{ contributor.repositories.length }} repos</span>
              </div>
              <a :href="contributor.html_url" target="_blank" rel="noopener noreferrer" class="block w-full text-center bg-blue-600 text-white text-sm py-2 rounded-md hover:bg-blue-700 transition duration-300 ease-in-out"> View Profile </a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from "vue";

const contributors = ref([]);
const loading = ref(true);
const error = ref(null);
const expandedCard = ref(null);

const CACHE_KEY = "t3volabs_contributors";
const CACHE_EXPIRATION = 15 * 24 * 60 * 60 * 1000; // 15 days in milliseconds

const mergeContributorData = (existingData, newData, repoName) => {
  const contributor = existingData || {
    ...newData,
    totalCommits: 0,
    repositories: [],
  };

  contributor.totalCommits += newData.contributions;
  if (!contributor.repositories.includes(repoName)) {
    contributor.repositories.push(repoName);
  }

  return contributor;
};

const saveToCache = (data) => {
  localStorage.setItem(CACHE_KEY, JSON.stringify({ timestamp: Date.now(), data }));
};

const getFromCache = () => {
  const cachedData = localStorage.getItem(CACHE_KEY);
  if (!cachedData) return null;

  const { timestamp, data } = JSON.parse(cachedData);
  return Date.now() - timestamp > CACHE_EXPIRATION ? null : data;
};

const fetchFreshData = async () => {
  const reposResponse = await fetch("https://api.github.com/orgs/t3volabs/repos");
  if (!reposResponse.ok) throw new Error("Failed to fetch repositories");
  const repos = await reposResponse.json();

  const contributorsMap = new Map();

  await Promise.all(
    repos.map(async (repo) => {
      const contributorsResponse = await fetch(`https://api.github.com/repos/t3volabs/${repo.name}/contributors`);
      if (contributorsResponse.ok) {
        const repoContributors = await contributorsResponse.json();
        repoContributors.forEach((contributor) => {
          const existing = contributorsMap.get(contributor.id);
          contributorsMap.set(contributor.id, mergeContributorData(existing, contributor, repo.name));
        });
      }
    })
  );

  return Array.from(contributorsMap.values()).sort((a, b) => b.totalCommits - a.totalCommits);
};

onMounted(async () => {
  try {
    const cachedData = getFromCache();

    if (cachedData) {
      contributors.value = cachedData;
    } else {
      const freshData = await fetchFreshData();
      contributors.value = freshData;
      saveToCache(freshData);
    }
  } catch (err) {
    error.value = "Failed to fetch contributor data. Please try again later.";
    console.error("Error:", err);
  } finally {
    loading.value = false;
  }
});
</script>

<style scoped>
.contributor-card {
  transform-origin: center;
  transition: all 0.3s ease;
}

.contributor-card.expanded {
  transform: scale(1.05);
  z-index: 10;
}

.bg-gradient-to-b {
  background-image: linear-gradient(to bottom, var(--tw-gradient-stops));
}
</style>
