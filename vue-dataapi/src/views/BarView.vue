<template>
  <div>
    <h1 class = "normal">Bar Graph</h1>
    <h2 class = "normal">Number of Programs in Library</h2>
    <div class = "bar">
    <template v-if="libraries.length > 0">
      <BarGraph :libraries="libraries" />
    </template> </div>
  </div>
</template>

<script setup>
import { ref, onBeforeMount } from 'vue';
import BarGraph from '../components/BarGraph.vue';

const libraries = ref([]);

async function getLibraries() {
  try {
    const response = await fetch('https://data.cityofnewyork.us/resource/ne9z-skhf.json');
    if (!response.ok) {
      throw new Error('Failed to fetch libraries');
    }
    libraries.value = await response.json();
  } catch (error) {
    console.error('Error fetching libraries', error);
  }
}

onBeforeMount(getLibraries);
</script>

<style scoped>
.normal{
  display: flex;
  flex-direction: row;
  justify-content: center;
  background-color: rgba(255, 255, 255, 0.575);
}

.bar{
  background-color: rgba(255, 255, 255, 0.774);
}
</style>