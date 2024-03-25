<template>
  <div>
    <h1>Bar Graph</h1>
    <h3>Number of Programs in Library</h3>
    <template v-if="libraries.length > 0">
      <BarGraph :libraries="libraries" />
    </template> 
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