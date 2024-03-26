<template>
  <div>
    <h1>Pie Graph</h1>
    <div class="dropdown">
      <select v-model="selectedOption">
        <option id="dropChoice" value="location">Location Data</option>
        <option  id="dropChoice" value="weeklyHours">Weekly Hours of Public Service</option>
      </select>
    </div>
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

<style scoped>
.dropdown {
  margin-left: 9.8vw;
}

#dropChoice {
  font-size: 1.2rem;
}
</style>