
<!-- <template>
  <div class="container">
    <Bar v-if="loaded" :data="chartData" />
  </div>
</template>

<script>
import { Bar } from 'vue-chartjs'
import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js'

ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)

export default {
  name: 'BarChart',
  components: { Bar },
  data: () => ({
    loaded: false,
    chartData: null
  }),
  async mounted () {
    this.loaded = false

    try {
      const { userlist } = await fetch('/api/userlist')
      this.chartdata = userlist

      this.loaded = true
    } catch (e) {
      console.error(e)
    }
  }
}
</script> -->

<template>
  <h1>Library Locations</h1>
  <div class="flexbox">
    <CoolData
      v-for="library in libraries"
      :key="library.branch"
      :library="library"
      :branch="library.branch"
      :boro="library.boro_central_library"
    />
  </div>
</template>

<script setup>
import { ref, onBeforeMount } from 'vue'
import CoolData from "../components/CoolData.vue"

const libraries = ref([])


async function getLibraries() {
  try {
    const response = await fetch('https://data.cityofnewyork.us/resource/ne9z-skhf.json')
    if (response.status !=200) {
      throw new Error('Failed to fetch')
    }
    libraries.value = await response.json()
  } catch (error) {
    console.error('Error fetching', error)
  }
}

onBeforeMount(async () => {
  await getLibraries()
})


/* import CoolData from '@/components/CoolData.vue';
export default {
  data() {
    return {
      libraries: [],
    };
    },
    mounted:function () {
      this.fetchData();
    },
    methods: {
      fetchData: async function () {
        try {
          const result = await fetch(
            `https://data.cityofnewyork.us/resource/ne9z-skhf.json`
          );
          const data = await result.json();
          this.libraries = data.results;
          console.log(data);
          

        } catch (error) {
          console.log(error);
        }
      }
    }
  } */

</script>

<style scoped>

h1 {
  text-align: center;
}
.flexbox {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  width: 100%;
  justify-items: center;
  justify-content: center;
  
}
</style>