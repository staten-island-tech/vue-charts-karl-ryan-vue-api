<template>
  <div>
    <h1>Pie Graph</h1>
  <select v-model="selectedOption">
    <option value="location">Location Data</option>
    <option value="weeklyHours">Weekly Hours of Public Service</option>
  </select>
    <template v-if="libraries.length > 0">
      <PieGraph :libraries="libraries" :selectedOption="selectedOption"/>
    </template> 
  </div>
</template>

<script setup>
import { ref, onBeforeMount } from 'vue';
import PieGraph from '../components/PieGraph.vue';

const libraries = ref([]);
const selectedOption = ref('location');

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