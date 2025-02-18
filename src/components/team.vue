<template>
  <div class="container mx-auto p-4 md:p-8">
    <h1 class="text-xl font-bold mb-8 text-center text-gray-800">T3VO Labs Team</h1>

    <div v-if="loading" class="flex items-center justify-center h-64">
      <div class="animate-spin rounded-full h-12 w-12 border-t-2 border-b-2 border-blue-500"></div>
    </div>

    <div v-else-if="error" class="text-center text-red-500 p-4">
      {{ error }}
    </div>

    <div v-else class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
      <div v-for="contributor in contributors" :key="contributor.id" class="bg-white rounded-lg shadow-lg overflow-hidden transform transition duration-300 hover:scale-105">
        <div class="relative pb-2/3">
          <img :src="contributor.avatar_url" :alt="contributor.login" class="absolute h-full w-full object-cover" />
        </div>
        <div class="p-6">
          <h3 class="text-xl font-semibold mb-2 text-gray-800">{{ contributor.login }}</h3>
          <div class="flex justify-between mb-4">
            <div class="text-center">
              <div class="text-2xl font-bold text-blue-600">{{ contributor.totalCommits }}</div>
              <div class="text-sm text-gray-600">Commits</div>
            </div>
            <div class="text-center">
              <div class="text-2xl font-bold text-green-600">{{ contributor.repositories.length }}</div>
              <div class="text-sm text-gray-600">Repos</div>
            </div>
          </div>
          <a :href="contributor.html_url" target="_blank" rel="noopener noreferrer" class="block w-full text-center bg-gray-800 text-white py-2 rounded-md hover:bg-gray-700 transition duration-300"> View Profile </a>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";

const contributors = ref([]);
const loading = ref(true);
const error = ref(null);

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
.pb-2\/3 {
  padding-bottom: 66.666667%;
}
</style>
